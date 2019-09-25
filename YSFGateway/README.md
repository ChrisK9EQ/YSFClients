YSF Gateway has been modified as follows:
2019-09-23:
An additional option has been added to the initialization file to disable remote control via RF and the WiRES-X function.
This has been done to allow an MMDVM-based hotspot to act as a bridge between a WiRES-X node and a YSF Reflector. Without this modification, both the node and the hotspot attempt to respond to RF WiRES-X commands.
[General]
WiresXDisable = 1

The YSF Gateway interfaces the MMDVM Host to the open source YSF Reflector system using the standard Wires-X commands from the radio. It also gateways position information to aprs.fi if sent.

The file YSFHosts.txt holds information about the reflectors available, and the gateway has the ability to reload this file at intervals to ensure that it is always up to date.

It is expected that a call to retrieve this file is done via some mechanism such as cron on Linux. The URLs to retrieve the latest file are [http://register.ysfreflector.de/export_csv.php](http://register.ysfreflector.de/export_csv.php), or [https://register.ysfreflector.de/export_csv.php](https://register.ysfreflector.de/export_csv.php).

An example would be following line in root's crontab, that fetches the reflector-list each 5 minutes:
> sudo crontab -e

add following line:

> */5 * * * * wget -O /var/YSFGateway/YSFHosts.txt http://register.ysfreflector.de/export_csv.php
