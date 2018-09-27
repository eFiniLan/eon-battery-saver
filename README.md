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

Then reboot your EON.

FAQ
===

**Q: What is EON?**

A: EON is a dashcam dev kit developed by [comma ai](https://comma.ai/).

**Q: Do I need this script?**

A: If you like me, suffering from flat battery due to not charging overnight or would like to reduce(possibility) the battery overheat issue, the script can probably help you too.

**Q: Why the UI becomes sluggish?**

A: This is due to the CPU max scale frequencies have been reduced to the smallest available, it will be gone once it's connected to USB.

**Q: Why the battery still reach high temp?**

A: I don't think the script will help much on reducing battery temp, my recommendation is to turn on the windscreen defog once EON is over 46 °C.

**Q: Once the CPU frequencies reduced, will that effect upload?**

A: I did notice higher CPU usage (through ```top``` command in ssh), other than that everything works like usual.