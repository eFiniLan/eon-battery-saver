eon-battery-saver
======
eon-battery-saver is written for comma EON, a dashcam dev kit.

basically it checks usb connection/battery %/battery temp every second:

* when no usb connection (not receving power from panda), it changes all cpu max scale freq to the lowest available to preserve battery.
* when battery % is high and battery temp is high, it stops charging to reduce battery temp.
* when battery % is low and battery temp is high, it starts charging to keep EON running.
* turn off a few wifi related configration to preserve battery.

Installation
======
Place this script in /data/openpilot/ and add this line to launch_openpilot.sh right after ```#!/usr/bin/bash```:

```
/system/bin/sh ./battery_saver.sh &
```
