# RG99
![Alt text](imgs/main.jpg)
  
## Introduction
Thanks Paul Cercueil and Opendingux development team. OpenDingux system is getting better and better. Based on OpenDingux resources, now, Linux OS can run on RG99 handheld. If you would like to port some emulators or games into this device, you can follow the build instrcution below, thanks !  
  
|Component|Description                                 |
|---------|--------------------------------------------|
|CPU      |Ingenic JZ4725B 360MHz                      |
|RAM      |32MB                                        |
|Storage  |256GB                                       |
|Screen   |2.8" 320x240                                |
|Slot     |MicroSD                                     |
|Gamepad  |DPad, 4 Buttons, M1, M2, Start, Select, L, R|
|USB      |Client                                      |
|Battery  |3.7V 1800mA                                 |
|Dimension|119mm x 82mm x 25mm                         |
|Weight   |325g                                        |
|Others   |Vibrator                                    |
  
## How to build Linux OS for RG99  
### prepare environment
-  Debian 9 (x64)
-  download all of sources in release page
  
### configure toolchain
-  extract toolchain_rg99.7z into /opt/rg99
-  export command
   -  export PATH=$PATH:/opt/rg99/usr/bin
   
### build buildroot
-  download buildroot.tar.gz from release page
-  command
   -  $ tar xvf buildroot.tar.gz
   -  $ cd buildroot
   -  $ make rg99_defconfig
   -  $ make
  
### build kernel
-  download kernel_v1.0.tar.gz from release page
-  command
   -  $ $ tar xvf kernel_v1.0.tar.gz
   -  $ cd kernel
   -  $ ARCH=mips CROSS_COMPILE=mipsel-linux- make rg99_defconfig
   -  $ ARCH=mips CROSS_COMPILE=mipsel-linux- make uzImage.bin dtbs -j8
  
### flash bootloader
-  download flasher.tar.gz from release page
-  put RG99 into boot mode (Press START and then power up)
-  plug USB into PC
-  command:
   -  $ sudo flash.sh
  
### flash system
-  download v1.0_sdcard.img.7z from release page
-  prepare 4GB MicroSD
-  flash sdcard.img into MicroSD
-  put MicroSD into RG99 and then power up
  
### https://steward-fu.github.io/website/index.htm
