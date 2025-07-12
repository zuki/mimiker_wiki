# テスト基盤

## テスtの実行

利用可能なテストをすべて実行したい場合は`./run_tests.py`を使ってください。
これは継続的インテグレーションで使用されるコマンドです。便利な引数を以下に
示します：

* `--infinite` - エラーが見つかるまでテストを続けます。
* `--non-interactive` - テストが失敗した場合、インタラクティブなGDBセッションを
  実行しません。
* `--thorough` - より多くのテストシードを生成します。テストにはより多くの時間が
  かかります。

より細かく制御するためにテストの実行を制御するカーネル引数を渡すことができます。
これには有用性が証明されているテストの並べ替えを生成するために使用される`seed`を
渡すことも含まれます。テストの実行を制御するための便利なカーネル引数を以下に
示します。


* `test=TEST` - 指定のテストを実行するようカーネルに要求します。
  `test=user_{name}`は単一のユーザーテストの実行を、`test={name}`は単一の
  カーネルテストの実行を要求します。
  `test=test1,test2,test3`のようにカンマ区切りで（スペースを入れずに）複数の
  テストを指定できます。
* `test=all` - 複数のテストを次々に実行し、すべてが合格した場合にのみ成功を
  報告します。
* `seed=UINT` - `test=all`を使用する際にテストのリストをシャッフルするための
  RNGシードを設定します。
* `repeat=UINT` - `test=all`を使用する際に各テストの（シャッフルされた）
  繰り返し回数を指定します。ユーザー指定のテストを実行する場合（すなわち、
  `test`が`all`でない場合）、`repeat`は各テストの実行回数を指定します。
  たとえば、`test=test1,test2 repeat=4`は`test1`を4回実行した後、`test2``を
  4回実行します。

## テストの実装

### カーネルテスト

`/sys/tests`にあります。
テスト関数のシグネチャは`{name}(void)`です。たまに`{name}(unsigned int)`の
場合もありますが、`(int (*)(void))`に強制する必要があります。

テストを登録する次のマクロがあります。

* `KTEST_ADD(name, func, flags)`
* `KTEST_ADD_RANDINT(name, func, flags, max)` - 関数ポインタを`(int (*)(void))`に
  キャストする必要があります。

ここで`name`はテスト名、`func`はテスト関数へのポインタ、`flags`は後述の通り、
`max`はテストに提要される最大のランダム引数です。

### ユーザテスト

`/bin/utest`にあります。
ユーザ空間のテスト関数のシグネチャは`int test_{name}(void)`であり、
`/bin/utest/utest.h`で定義されている必要があります。
テストを実行可能にするためには次の行のいずれかを`/sys/tests/utest.c`に
追加する必要があります。

* `UTEST_ADD_SIMPLE({name})` - アサーションまたはゼロ以外の返り値でテストが失敗します。
* `UTEST_ADD_SIGNAL({name}, {SIGNUMBER})` - `{SIGNUMBER}`で終了するとテストはパスします。
* `UTEST_ADD({name}, {exit status}, flags)` - ステータス`{exit status}`で終了するとテストにパスします。

また、次の行を追加する必要があります。

*  `/bin/utest/main.c`に`CHECKRUN_TEST({name})`,
*  `/bin/utest/utest.h`に`int test_{name}(void);`
*  `bin/utest/Makefile`に`${filename}.c`

### テストの作成

テストは0を返すか、実行中にカーネルパニックを起こすものですが、これは`assert`を
使うことで実現できます。つまり、テストは以下のようなコードではいけないと
いうことです。

```c
pid_t child_pid;
switch (child_pid = fork())
{
case -1: /* error */
    perror("fork");
    exit(EXIT_FAILURE);

case 0:
    /* child */
    ...

default:
    /* parent */
    ...
}
```

次のようにします。

```c
pid_t child_pid = fork();
assert(child_pid >= 0);
if (child_pid == 0) {
  /* child */
  ...
}
/* parent */
...
```

正常に実行されない可能性のあるあらゆる関数の使用についても同様です。

また、`assert`も要注意です。*assertはマクロ*なので中の式が複数回実行される
可能性があります。そのため、以下の`fork`バージョンは絶対に**許されません**。

```c
pid_t child_pid;
assert(child_pid = fork() >= 0);
if (child_pid == 0) {
  /* child */
  ...
}
/* parent */
...
```

### フラグ

* `KTEST_FLAG_NORETURN` - テストは復帰しないことを意味します。
* `KTEST_FLAG_DIRTY` - テストがカーネル内部の状態を不可逆的に破壊し、
  カーネルを再起動することなくそれ以降のテストを実施しても結論は出ない
  ことを意味します。
* `KTEST_FLAG_USERMODE` - テストがユーザモードに入ることを示します。
* `KTEST_FLAG_BROKEN` - 自動モードでのテストの実行を除外します。このフラグは
  テストフレームワークのデバッグ中に一時的にテストをマークする場合にのみ
  有用です。
* `KTEST_FLAG_RANDINT` - テストがランダムな整数を引数として受け取りたい
  ことを示します。
