# `sys/kern/*.c`

| ファイル名 | 内容 |
|------------|:-------|
| Makefile | このディレクトリのMakefile |
| bus.c | バス(MMIO/IO)空間にあるハードウェアの読み書きを行う汎用の関数を提供 |
| callout.c | コールアウト（タイマー）を処理 |
| clock.c | システムクロック（clock, profclock）を設定 |
| cmdline.c | カーネルコマンドラインの解析に使用されるボード共通初期化コード |
| condvar.c | 条件変数を実装 |
| console.c | コンソール関数（初期化、入出ろ）を実装 |
| cred.c | 利用者権限（クレデンシャル）を処理 |
| cred_checks.c | ファイル関係の権限チェック |
| cred_syscalls.c | 利用者権限関係のシステムコールを実装 |
| dev_null.c | /dev/null, /dev/zero の実装 |
| dev_procstat.c | /dev/procstatの実装 |
| devclass.c | デバイスクラスの実装（作成、検索など） |
| devfs.c | デバイスファイルシステムの実装 |
| device.c | デバイスの処理（プローブ、アタッチ、デタッチなど）とリソース管理 |
| event.c | kqueue1, kenventシステムコールの実装 |
| exec.c | execve()システムコールの実装 |
| exec_elf.c | ELFファイルを読み込む |
| exec_shebang.c | スクリプトファイルのインタプリタ部分（シェバング）を読み込む |
| fdt.c |  |
| file.c |  |
| file_syscalls.c |  |
| filedesc.c |  |
| fork.c | do_fork()の実装 |
| initrd.c |  |
| interrupt.c |  |
| kasan.c |  |
| kasan_quar.c |  |
| kcsan.c |  |
| kenv.c |  |
| kern.ka |  |
| kgprof.c |  |
| klog.c |  |
| kmem.c |  |
| ktest.c |  |
| lockdep.c |  |
| main.c |  |
| malloc.c |  |
| mcount.c |  |
| mmap.c |  |
| mutex.c |  |
| pcpu.c | CPUのプライベートデータを宣言 |
| pipe.c |  |
| pool.c |  |
| proc.c |  |
| pty.c |  |
| ringbuf.c |  |
| runq.c |  |
| sbrk.c |  |
| sched.c |  |
| signal.c |  |
| sleepq.c |  |
| sys_kern_c.txt |  |
| syscalls.c |  |
| syscalls.conf |  |
| syscalls.master |  |
| sysent.h |  |
| thread.c |  |
| time.c |  |
| timer.c | タイマーを処理（初期化、予約、実行、解除など）する |
| tmpfs.c |  |
| tty.c |  |
| turnstile.c |  |
| uart_tty.c |  |
| uio.c |  |
| ustack.c |  |
| vfs.c |  |
| vfs_name.c |  |
| vfs_readdir.c |  |
| vfs_syscalls.c |  |
| vfs_vnode.c |  |
| vm_amap.c |  |
| vm_map.c | 仮想アドレスマップ、マップエントリの操作 |
| vm_physmem.c |  |
| vmem.c |  |
