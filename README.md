# backbright-control
This simple module allows for backlight control of your intel_baclight in the command line.
This script only works with systems that use intel_backlight. acpi0_video is NOT supported.
To see which your system uses, run the following command:
`$ ls /sys/class/backlight`

Feel free to clone this module and use/share/edit it.

# Notes
I have made this module because I updated my system to use my dedicated graphics card. That resulted in xbacklight not supporting backlight changes anymore.
This is basically the first "big" bash script that I wrote. Any feedback is welcome and gladly appreciated, either here on GitHub or email.

# How this script works:
`backbright-control` only uses 2 parameters. `-m` for mode and `-v` for value.

`-m` supports as input `increase`, `i`, `decrease` and `d`. These represent whether you want your screen to brighten up or down.
`-v` uses a value. I recommend you test this input with multiple values to find the one that best fits your use. I will explain this in a later paragraph.

Example: `backbright-control -m i -v 750` to increase the screens brightness with a raw value of 750.

# How minimum and maximum values are calculated
The maximum value of the screens brightness is calculated by reading `/sys/class/backlight/intel_backlight/max_brightness`.
The minimum value is calculated by taking the max value of the screen and dividing that by 20. If you feel like that isn't enough, or maybe too much for you, I recommend you cange this value to a bigger or smaller one.
You could even try to put in a hardcoded value. I recommend not putting it to 0, as that might completely turn off your backlight, resulting in a screen that seems like it's off.

# Binding this script to keyboard keys
You can try to bind this script to your keyboard using `xbindkeys`.
Read the respective documentation for that to do this.

