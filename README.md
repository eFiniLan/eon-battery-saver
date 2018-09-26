eon-battery-saver
======
eon-battery-saver is written for comma EON, a dashcam dev kit.

basically it checks USB connection/battery %/battery temp every second:

* when no USB connection (not receiving power from panda), it changes all CPUs' max scale freq to the lowest available to preserve battery.
* when battery % is high and battery temp is high, it stops charging to reduce battery temp.
* turn off a few WIFI related configurations to preserve battery.

Installation
======
Place this script in /data/openpilot/ and add this line to launch_openpilot.sh right after ```#!/usr/bin/bash```:

```
/system/bin/sh ./battery_saver.sh &
```
