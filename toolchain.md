ツールチェーン
---

Mimikerをビルド・実行するには、コンパイラ、リンカ、ELFツール、エミュレータ、
デバッガなどのツールチェーンが必要です。デフォルトのオプションは最新の
_LLVMツールチェーン_ （[tools.mk][6]でバージョンをチェック）、すなわち、
[apt.llvm.org][7]が提供している`clang`, `lld`, `llvm`と[QEMU][11]です。

注意:

MimikerをMIPSで実行する場合はパッチを当てたバージョンのQEMUもインストール
する必要があります。このバージョンはメインストリームバージョンでは修正されて
いないいくつかの問題を解決しています。[patches][10]リストを参照してください。
Debian x86-64用のプリビルドパッケージは[ここ][5]にあります。

## 必要なソフトウェア

必要なソフトウェアは[Dockerfile][12]に書かれています。また、Debianシステムに
必要なすべてのソフトウェアを自動的にインストールするスクリプト
[install-tools.sh][13]もあります。

pythonのモジュールもインストールする必要があります。次のコマンドでインストール
できます。

```
pip3 install -r requirements.txt
```

#### Dockerfileにある依存関係についてのコメント

```
# patchとquiltは、luaとcontrib/gperfの
# プログラムでで必要です。
# launchとtmuxはLauchで必要です。
```

## 非推奨ツールチェーン

もう1つの方法はカスタムビルドされた _GNUツールチェーン_、すなわち、
`gcc`, `binutils`, `gdb`を使う方法です。Debian x86-64ベースのシステム用に
[MIPS][1], [AArch64][2], RISC-Vの[32-bit][3]と[64-bit][4]に対応した
パッケージを用意しました。

[1]: http://mimiker.ii.uni.wroc.pl/download/mipsel-mimiker-elf_latest_amd64.deb
[2]: http://mimiker.ii.uni.wroc.pl/download/aarch64-mimiker-elf_latest_amd64.deb
[3]: http://mimiker.ii.uni.wroc.pl/download/riscv32-mimiker-elf_latest_amd64.deb
[4]: http://mimiker.ii.uni.wroc.pl/download/riscv64-mimiker-elf_latest_amd64.deb
[5]: http://mimiker.ii.uni.wroc.pl/download/qemu-mimiker_latest_amd64.deb
[6]: ../../mimiker/build/tools.mk
[7]: https://apt.llvm.org/
[8]: https://packages.debian.org/sid/gdb-multiarch
[9]: ../../mimiker/launch
[10]: ../../mimiker/toolchain/qemu-mimiker/patches
[11]: https://www.qemu.org/
[12]: ../blob/master/Dockerfile
[14]: ../blob/master/install-tools.sh
