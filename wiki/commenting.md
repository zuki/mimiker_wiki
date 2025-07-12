# どのようにコードをコメントするのか？

- Cスタイルのコメントの中に[Markdown](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)構文を使用してコメントします。

## タグ

タグはコードの中で重要なことをマークするためのものです。特別な注意を必要と
するコメントを書く場合は適切なタグを追加してください。

次のワイルドカードを使用します。

- `?a`: 作者のGitHubニックネーム
- `?s`: コードの引用元のソース名
- `?t`: 記述する用語

### タグ一覧

- `FIXME(?a)`: 必要な修正についての情報。承知しているがそのままにしているもの
- `TODO(?a)`: GitHubのIssueにするほどではない、当面は未実装の機能に関する情報
- `XXX(?a)`: おそらくはハックであるコードの明白でない部分の説明
- `START OF ?s CODE` と `END OF ?s CODE`: 外部から取り込んだコードの部分を
  マークする。そのコードをどこから取得したかに関する情報をリンクとともに
  残す**必要があります**。
- `INFO(?t)`: 指定された用語の説明。コードの中に書くのは一回だけでなければなりません。

### タグの使用例

- `FIXME(?a)`

```c=
/* Find the first free number for that device.
 * FIXME Not the best solution, but will do for now. */
do {
    snprintf(buf, sizeof(buf), "event%d", unit);
    ret = devfs_makedev(evdev_input_dir, buf, &evdev_vnodeops, evdev, NULL);
    unit++;
} while (ret == EEXIST);
```

[完全なコード](https://github.com/cahirwpz/mimiker/blob/eacc19512e859e5203b8345963b3b71c96dacf53/sys/drv/evdev.c#L614-L621)

- `TODO(?a)`

```c=
char *ttyname(int fd) {
   /* TODO(fzdob): to implement */
   errno = ENOTTY;
   return NULL;
 }
```

```c=
static void cbus_uart_init(console_t *dev __unused) {
    /* TODO(pj) This resource allocation should be done in parent of
     * cbus_uart device. Unfortunately now we don't have fully working device
     * infrastructure. It should be changed after done with DEVCLASS. */
    vaddr_t handle = kmem_map_contig(MALTA_FPGA_BASE, PAGESIZE, PMAP_NOCACHE);
    cbus_uart->r_bus_handle = handle + MALTA_CBUS_UART_OFFSET;

    set(LCR, LCR_DLAB);
    out(DLM, 0);
    out(DLL, 1); /* 115200 */
    clr(LCR, LCR_DLAB);

    out(IER, 0);
    out(FCR, 0);
    out(LCR, LCR_8BITS); /* 8-bit data, no parity */
  }
```

```c=
static intr_filter_t mips_timer_intr(void *data) {
    device_t *dev = data;
    mips_timer_state_t *state = dev->state;
    /* TODO(cahir): can we tell scheduler that clock ticked more than once? */
    (void)set_next_tick(state);
    tm_trigger(&state->timer);
    return IF_FILTERED;
  }
```

```c=
/* TODO(cahir): revisit this after off_t is changed to int64_t */
    if ((unsigned long)pos > LONG_MAX) {
      errno = EOVERFLOW;
      return -1L;
    }
```

- `XXX(?a)`

```c=
/* XXX: It's still possible for periods to be lost.
* For example disabling interrupts for the whole period
* without calling pit_gettime will lose period_ticks.
* It is also possible that time suddenly jumps by period_ticks
* due to the fact that pit_update_time() can't detect an overflow if
* the current counter value is greater than the previous one, while
* pit_intr() can thanks to the noticed_overflow flag. */
pit_update_time(pit);
if (!pit->noticed_overflow)
 pit_incr_ticks(pit, pit->period_ticks);
tm_trigger(&pit->timer);
```

[下の例のコンテキスト](https://github.com/cahirwpz/mimiker/blob/eacc19512e859e5203b8345963b3b71c96dacf53/lib/libc/stdio/vfscanf.c#L923-L937)

```c
#if 1 /* XXX another disgusting compatibility hack */
```

- `START OF ?s CODE` / `END OF ?s CODE`

[例](https://github.com/cahirwpz/mimiker/blob/eacc19512e859e5203b8345963b3b71c96dacf53/sys/kern/tty.c#L26-L113)

- `INFO(?a)`

<!-- TODO(hadarai) add INFO example -->
