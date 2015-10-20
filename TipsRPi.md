# TipsRPi
Tips and Tricks Raspberry Pi 2


Controlling power and activity LED:

  green OK LED (GPIO 47): /sys/class/leds/led0/
  red PWR LED (GPIO 35): /sys/class/leds/led1/

  Blinking:

    echo heartbeat > /sys/class/leds/led0/trigger
    echo heartbeat > /sys/class/leds/led1/trigger
    
  Default value:

    echo mmc0 > /sys/class/leds/led0/trigger
    echo input > /sys/class/leds/led1/trigger   <= TBC


Mounting .img:

  Find the offset of the img:

  fdisk -lu image.img

    $ fdisk -lu hypriot-rpi-20150416-201537.img
    Disk hypriot-rpi-20150416-201537.img: 1.2 GiB, 1280000000 bytes, 2500000 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disklabel type: dos
    Disk identifier: 0x00000000

    Device                           Boot  Start     End Sectors   Size Id Type
    hypriot-rpi-20150416-201537.img1        2048  133119  131072    64M  c W95 FAT32 (LBA)
    hypriot-rpi-20150416-201537.img2      133120 1999999 1866880 911.6M 83 Linux
  
  In this example:

    Boot partition start at 2048x512=1048576
    System partition start at 133120x512=68157440

  Mount command:
    
    $ sudo mkdir /mnt/boot
    $ sudo mount -t vfat -o loop,offset=1048576 hypriot-rpi-20150416-201537.img /mnt/boot/

    $ sudo mkdir /mnt/system
    $ sudo mount -t ext4 -o loop,offset=68157440 hypriot-rpi-20150416-201537.img /mnt/system/

  Umunt command:

    $ sudo umount /mnt/boot/
    $ sudo umount /mnt/system/

  Alternative:

    sudo kpartx -av image.img

    Mount:

    $ sudo kpartx -av hypriot-rpi-20150416-201537.img
    add map loop0p1 (253:11): 0 131072 linear /dev/loop0 2048
    add map loop0p2 (253:12): 0 1866880 linear /dev/loop0 133120
    $ sudo mount /dev/mapper/loop0p1 /mnt/boot/
    $ sudo mount /dev/mapper/loop0p2 /mnt/system/

    Umount:

    $ sudo umount /mnt/boot/
    $ sudo umount /mnt/system/
    $ sudo kpartx -d hypriot-rpi-20150416-201537.img
    
