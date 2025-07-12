# 実機で実行

## `config.txt`

```bash
kernel=mimiker.img
arm_64bit=1
kernel_address=0x200000
enable_uart=1
uart_2ndstage=1
ramfsfile="initrd.cpio"
```

### 実行結果1

```
Raspberry Pi Bootcode
Read File: config.txt, 110
Read File: start.elf, 2977280 (bytes)
Read File: fixup.dat, 7266 (bytes)
MESS:00:00:01.102245:0: brfs: File read: /mfs/sd/config.txt
MESS:00:00:01.106422:0: brfs: File read: 110 bytes
MESS:00:00:01.143229:0: HDMI0:EDID error reading EDID block 0 attempt 0
MESS:00:00:01.149396:0: HDMI0:EDID error reading EDID block 0 attempt 1
MESS:00:00:01.155732:0: HDMI0:EDID error reading EDID block 0 attempt 2
MESS:00:00:01.162069:0: HDMI0:EDID error reading EDID block 0 attempt 3
MESS:00:00:01.168405:0: HDMI0:EDID error reading EDID block 0 attempt 4
MESS:00:00:01.174742:0: HDMI0:EDID error reading EDID block 0 attempt 5
MESS:00:00:01.181079:0: HDMI0:EDID error reading EDID block 0 attempt 6
MESS:00:00:01.187416:0: HDMI0:EDID error reading EDID block 0 attempt 7
MESS:00:00:01.193752:0: HDMI0:EDID error reading EDID block 0 attempt 8
MESS:00:00:01.200089:0: HDMI0:EDID error reading EDID block 0 attempt 9
MESS:00:00:01.206184:0: HDMI0:EDID giving up on reading EDID block 0
MESS:00:00:01.212608:0: brfs: File read: /mfs/sd/config.txt
MESS:00:00:01.440413:0: gpioman: gpioman_get_pin_num: pin DISPLAY_DSI_PORT not d
MESS:00:00:01.448793:0: *** Restart logging
MESS:00:00:01.451280:0: brfs: File read: 110 bytes
MESS:00:00:01.456605:0: hdmi: HDMI0:EDID error reading EDID block 0 attempt 0
MESS:00:00:01.463896:0: hdmi: HDMI0:EDID error reading EDID block 0 attempt 1
MESS:00:00:01.470754:0: hdmi: HDMI0:EDID error reading EDID block 0 attempt 2
MESS:00:00:01.477612:0: hdmi: HDMI0:EDID error reading EDID block 0 attempt 3
MESS:00:00:01.484470:0: hdmi: HDMI0:EDID error reading EDID block 0 attempt 4
MESS:00:00:01.491326:0: hdmi: HDMI0:EDID error reading EDID block 0 attempt 5
MESS:00:00:01.498185:0: hdmi: HDMI0:EDID error reading EDID block 0 attempt 6
MESS:00:00:01.505043:0: hdmi: HDMI0:EDID error reading EDID block 0 attempt 7
MESS:00:00:01.511900:0: hdmi: HDMI0:EDID error reading EDID block 0 attempt 8
MESS:00:00:01.518758:0: hdmi: HDMI0:EDID error reading EDID block 0 attempt 9
MESS:00:00:01.525373:0: hdmi: HDMI0:EDID giving up on reading EDID block 0
MESS:00:00:01.531277:0: hdmi: HDMI0:EDID error reading EDID block 0 attempt 0
MESS:00:00:01.539070:0: hdmi: HDMI0:EDID error reading EDID block 0 attempt 1
MESS:00:00:01.545928:0: hdmi: HDMI0:EDID error reading EDID block 0 attempt 2
MESS:00:00:01.552786:0: hdmi: HDMI0:EDID error reading EDID block 0 attempt 3
MESS:00:00:01.559644:0: hdmi: HDMI0:EDID error reading EDID block 0 attempt 4
MESS:00:00:01.566501:0: hdmi: HDMI0:EDID error reading EDID block 0 attempt 5
MESS:00:00:01.573359:0: hdmi: HDMI0:EDID error reading EDID block 0 attempt 6
MESS:00:00:01.580216:0: hdmi: HDMI0:EDID error reading EDID block 0 attempt 7
MESS:00:00:01.587074:0: hdmi: HDMI0:EDID error reading EDID block 0 attempt 8
MESS:00:00:01.593932:0: hdmi: HDMI0:EDID error reading EDID block 0 attempt 9
MESS:00:00:01.600547:0: hdmi: HDMI0:EDID giving up on reading EDID block 0
MESS:00:00:01.606161:0: hdmi: HDMI:hdmi_get_state is deprecated, use hdmi_get_dd
MESS:00:00:01.614907:0: HDMI0: hdmi_pixel_encoding: 162000000
MESS:00:00:01.620619:0: vec: vec_middleware_power_on: vec_base: 0x7e806000 rev-0
MESS:00:00:01.637395:0: kernel=mimiker.img
MESS:00:00:01.644872:0: dtb_file 'bcm2710-rpi-3-b-plus.dtb'
MESS:00:00:01.650770:0: brfs: File read: /mfs/sd/bcm2710-rpi-3-b-plus.dtb
MESS:00:00:01.655863:0: Loaded 'bcm2710-rpi-3-b-plus.dtb' to 0x100 size 0x674
MESS:00:00:01.663889:0: brfs: File read: 1652 bytes
MESS:00:00:01.673828:0: dterror: no symbols found
MESS:00:00:01.677325:0: dterror: no symbols found
MESS:00:00:01.682258:0: brfs: File read: /mfs/sd/config.txt
MESS:00:00:01.687962:0: brfs: File read: 110 bytes
MESS:00:00:01.691549:0: Failed to open command line file 'cmdline.txt'
MESS:00:00:01.697845:0: dterror: no symbols found
MESS:00:00:01.703417:0: dterror: no symbols found
MESS:00:00:01.707029:0: dterror: no symbols found
MESS:00:00:01.710933:0: gpioman: gpioman_get_pin_num: pin EMMC_ENABLE not defind
MESS:00:00:02.239379:0: dterror: no symbols found
MESS:00:00:02.242669:0: dterror: no symbols found
MESS:00:00:02.247096:0: dterror: no symbols found
MESS:00:00:02.251522:0: dterror: no symbols found
MESS:00:00:02.255950:0: dterror: no symbols found
MESS:00:00:02.260376:0: dterror: no symbols found
MESS:00:00:02.271318:0: dterror: no symbols found
MESS:00:00:02.274758:0: dterror: no symbols found
MESS:00:00:02.279828:0: vchiq: Incorrect cache_line_size value - may cause datan
MESS:00:00:02.287216:0: dterror: no symbols found
MESS:00:00:02.324317:0: brfs: File read: /mfs/sd/mimiker.img
MESS:00:00:02.328259:0: Loaded 'mimiker.img' to 0x200000 size 0x75a70
MESS:00:00:02.334432:0: Device tree loaded to 0x2efff200 (size 0xd9f)
MESS:00:00:02.341889:0: uart: Set PL011 baud rate to 103448.300000 Hz
MESS:00:00:02.348274:0: uart: Baud rate change done...
MESS:00:00:02.351687:0: uart: Baud rate
```

## 修正

1. uartで止まるのはbtが邪魔をしているかららしい（[情報ソース1](https://forums.raspberrypi.com/viewtopic.php?t=270511), [情報ソース2](https://github.com/raspberrypi/firmware/issues/1618)）。

    a. dtbとoverlaysをraspi提供のものにする
    b. lauchで行っている`chosen`ノードの追加を`mimiker.dtsi`として切り出してコンパイルして
       overlaysに追加（makeすると`inux,initrd-end`の値が変わる場合があるのでlauchを修正して
       `mimiker.dtsi`に反映させる方法を考える）
2. config.txtを以下の通り変更

    ```bssh
    ernel=mimiker.img
    arm_64bit=1
    kernel_address=0x200000
    enable_uart=1
    init_uart_baud=115200
    uart_2ndstage=1
    initramfs initrd.cpio 0x8000000
    dtoverlay=disable-bt
    dtoverlay=mimiker
    ```

3. comdline.txtを追加

    ```
    console=serial0
    ```

4. SDカードの内容

    ```bash
    /Volume/NO\ NAME
    ├── COPYING.linux
    ├── LICENCE.broadcom
    ├── bcm2710-rpi-3-b-plus.dtb
    ├── bootcode.bin
    ├── cmdline.txt
    ├── config.txt
    ├── fixup.dat
    ├── initrd.cpio
    ├── mimiker.dtb
    ├── mimiker.img
    ├── overlays
    │   ├── disable-bt.dtbo
    │   └── mimiker.dtbo
    └── start.elf
    ```

### 実行結果2

```bash
... [省略]
MESS:00:00:01.540477:0: hdmi: HDMI:hdmi_get_state is deprecated, use hdmi_get_display_state instead
MESS:00:00:01.549223:0: HDMI0: hdmi_pixel_encoding: 162000000
MESS:00:00:01.554936:0: vec: vec_middleware_power_on: vec_base: 0x7e806000 rev-id 0x00002708 @ vec: 0x7e806100 @ 0x00000
MESS:00:00:02.194130:0: brfs: File read: /mfs/sd/initrd.cpio
MESS:00:00:02.198098:0: Loaded 'initrd.cpio' to 0x8000000 size 0x92e200
MESS:00:00:02.204449:0: initramfs loaded to 0x8000000 (size 0x92e200)
MESS:00:00:02.210595:0: kernel=mimiker.img
MESS:00:00:02.214417:0: brfs: File read: 9626112 bytes
MESS:00:00:02.223793:0: dtb_file 'bcm2710-rpi-3-b-plus.dtb'
MESS:00:00:02.232046:0: brfs: File read: /mfs/sd/bcm2710-rpi-3-b-plus.dtb
MESS:00:00:02.237136:0: Loaded 'bcm2710-rpi-3-b-plus.dtb' to 0x100 size 0x843b
MESS:00:00:02.259279:0: brfs: File read: 33851 bytes
MESS:00:00:02.291747:0: brfs: File read: /mfs/sd/config.txt
MESS:00:00:02.295750:0: brfs: File read: 178 bytes
MESS:00:00:02.302138:0: brfs: File read: /mfs/sd/overlays/disable-bt.dtbo
MESS:00:00:02.323904:0: Loaded overlay 'disable-bt'
MESS:00:00:02.362380:0: brfs: File read: 1073 bytes
MESS:00:00:02.366316:0: brfs: File read: /mfs/sd/overlays/mimiker.dtbo
MESS:00:00:02.375777:0: Loaded overlay 'mimiker'
MESS:00:00:02.389733:0: brfs: File read: 330 bytes
MESS:00:00:02.393495:0: brfs: File read: /mfs/sd/cmdline.txt
MESS:00:00:02.398211:0: Read command line from file 'cmdline.txt':
MESS:00:00:02.404102:0: 'console=serial0'
MESS:00:00:02.517887:0: gpioman: gpioman_get_pin_num: pin EMMC_ENABLE not defined
MESS:00:00:02.586422:0: brfs: File read: 16 bytes
MESS:00:00:02.624709:0: brfs: File read: /mfs/sd/mimiker.img
MESS:00:00:02.628670:0: Loaded 'mimiker.img' to 0x200000 size 0x75a70
MESS:00:00:02.634846:0: Device tree loaded to 0x2eff7800 (size 0x878d)
MESS:00:00:02.643456:0: uart: Set PL011 baud rate to 103448.300000 Hz
MESS:00:00:02.649748:0: uart: Baud rate change done...
MESS:00:00:02.653181:0: uart: Baud rate change done...
MESS:00:00:02.658807:0: gpioman: gpioman_get_pin_num: pin SDCARD_CONTROL_POWER not defined
```

- いくつかエラーは出ているが、このエラーは稼働システムでも出るようなのでここまでは
  問題はないと思われる。
- そもそもmimikerにファイルシステムがないように思われる。QEMUでramfsが動いているのは
  QEMUが頑張っているからなのか。次はこの点を調査する。

- QEMUのオプション

```bash
-nodefaults -icount shift=3,align=off,sleep=on -rtc clock=vm -kernel sys/mimiker.img.gz -initrd initrd.cpio -gdb tcp:127.0.0.1:26294,server,wait -serial none -machine raspi3b -smp 4 -cpu cortex-a53 -serial tcp:127.0.0.1:25151,server,wait -dtb launch.dtb -display none
```
