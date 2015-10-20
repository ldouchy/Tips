# TipsLinux
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
