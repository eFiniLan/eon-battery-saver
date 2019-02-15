Most mods are blocked/disabled after openpilot v0.5.7
======

eon-battery-saver
======
eon-battery-saver is written for comma EON, a dashcam dev kit.

basically it checks USB connection/battery %/battery temp every second:

* When no USB connection (not receiving power from panda), it changes all CPUs' max scale freq to the lowest available to preserve battery.
* When battery % is high and battery temp is high, it stops charging to reduce battery temp.
* Turn off a few WIFI related configurations to preserve battery.
* Turn off device after idle 3 hrs (no USB connection).

The battery usage is roughly 3-4% per hour (no upload, running on WIFI) with this script and about 10% per hour without it.

Installation
======
Place this script in:
```
/data/data/com.termux/files/
```
and add this line to ```/data/data/com.termux/files/continue.sh``` right after ```#!/usr/bin/bash```:

```
/system/bin/sh /data/data/com.termux/files/battery_saver.sh &
```

Then reboot your EON.

FAQ
===

**Q: What is EON?**

A: EON is a dashcam dev kit developed by [comma ai](https://comma.ai/).

**Q: Do I need this script?**

A: If you like me, suffering from flat battery due to not charging overnight or would like to reduce(possibility) the battery overheat issue, the script can probably help you too.

**Q: Why the UI becomes sluggish?**

A: This is due to the CPU max scale frequencies have been reduced to the minimum available, it will be gone once it's connected to a powered USB port.

**Q: Why the battery still reach high temp?**

A: I don't think the script will help much on reducing battery temp, my recommendation is to turn on the windscreen defog once EON is over 46 °C.

**Q: Once the CPU frequencies reduced, will that effect upload?**

A: I did notice higher CPU usage (through ```top``` command in ssh), other than that everything works like usual.
