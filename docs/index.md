# ZX909 tracker research

This site records reproducible, evidence-based research into the ZX909 family of
4G GPS trackers. It focuses on USB access, firmware preservation, LTE behavior,
and a path toward configurable MQTT telemetry.

## Current status

The tracker has been restored to its original ASR firmware and boots normally.
After the latest full original-image write, it reported measurable LTE signal
(`CSQ 16`) but did not register on O2 Germany or attach for packet data. A
separate LTE USB stick on the same local O2 network registered and found the
same nearby cell as a phone. This makes a tracker-specific issue plausible, but
does not prove that modem firmware alone is at fault: RF performance,
calibration/NVM, firmware configuration, and device or SIM policy remain
possible factors.

No Python environment has been verified running on the tracker, and MQTT has
not been demonstrated on it.

## Guides

- [Hardware and USB identification](hardware-usb.md)
- [AT command notes](at-commands.md)
- [Firmware backup and restore](firmware-restore.md)
- [LTE findings](lte.md)
- [MQTT development path](mqtt.md)
- [Research sources and tools](sources-tools.md)

## Safety and privacy

Use only firmware images made for the exact hardware. Keep a verified original
image before writing flash. This public guide intentionally omits firmware
images, device and subscriber identifiers, private broker settings, credentials,
and host-specific paths. Do not publish raw modem output without redacting
IMEI, IMSI, ICCID, serial number, cell identity, and location details.
