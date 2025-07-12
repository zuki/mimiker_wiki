# AArch64版の起動シーケンス

1. **_ENTRY(_start)**: sys/aarch64/start.S
   - Linux aarch64イメージの作成
   - cpu0以外を止める
   - 初期スタックの設定
   - call aarch64_init()
2. **aarch64_init(dtb)**: sys/aarch64/boot.c
   - drop_to_el1(): EL1への移行
   - configure_cpu(): cpuの構成
   - boot_clear(): bss領域のクリア
   - boot_sbrk_init(): ヒープ領域の初期化
   - dtbのコピー
   - build_page_table(): ページテーブルの作成
   - enable_mmu(): MMUの有効化
   - call aarch64_boot()
3. **aarch64_boot(dtb, pde, sbrk_end, vma_end)**: sys/aarch64/boot.c
   - FDT_init(dtb): デバイツリーの初期化
   - ダイレクトマップの設定
   - call board_init()
4. **board_init()**: sys/aarch64/board.c
   - init_klog(): klogの初期化
   - intr_enable(): 割り込みの有効化
   - rpi3_physmem(): カーネルとinitrd用の物理メモリの設定
   - call kernel_init()
5. **kernel_init()**: sys/kern/main.c
   - init_pmap(): カーネルページメモリマップの初期化
   - init_vm_page(): バディアロケータで管理されるvm_page構造体を割り当てる
   - init_pool(): プール（スラブキャッシュ）の初期化
   - init_vmem(): 汎用リソースアロケータの初期化
   - init_kmem(): カーネル仮想アドレス空間アロケータとマネージャの初期化
   - init_kmalloc(): kmallocの初期化
   - init_cons(): コンソールの初期化

   5.1 ディスパッチャとスケジューラ構造体を使用可能な状態にする
   - init_sleepq(): スリープキューの初期化
   - init_turnstile(): ターンスタイルの初期化
   - lockdep_init(): Kernel Lock Dependency Checkerの初期化 (if LOCKDEP=1)
   - init_thread0(): システムの最初のスレッドであるthread0の初期化
   - init_sched(): スケジューラの初期化

   5.2 スケジューラの準備ができたので、必要なスレッドを作成できる
   - init_callout(): コールアウト機構の初期化
   - preempt_enable(): プリエンプションの有効化

   5.3 FIRST_PASS初期化
   - init_devices(): デバイスの初期化とドライバのアタッチ
   - init_vfs(): vfs機構の初期化
   - init_proc(): プロセスの初期化
   - init_proc0(): プロセス0の初期化

   5.4 ファイルシステム（devfsを含む）のマウント
   - mount_fs(): 初期ファイルシステム(initrd, devfs, tmpfs)のマウント
   5.5 その他の初期化
   - init_clock(): クロックの初期化
   - init_kgprof(): カーネルプロファイリングの初期化 (if KGPROF=1)
   - klog("Kernel initialized!"); カーネルの初期化が完了
   5.6 initスレッドの作成とスケジューラ開始
   - init_kcsan(): Kernel Concurrency Sanitizerの初期化 (if KCSAN=1)
   - do_fork(start_init, NULL, &init_pid): initスレッドの作成してスケジューラに登録
   - sched_run(): 呼び出しスレッドをアイドルスレッドにする
