# Hardware and USB identification

## Observed identifiers

The tracker has appeared in these USB modes:

| Mode | USB ID | Observed product | Interface |
|---|---|---|---|
| ASR AROM boot port | `2ecc:3004` | Arom Usb Boot Port | CDC ACM serial |
| Normal tracker firmware | `2ecc:3010` | Mobile Composite Device Bus | Composite USB |
| QuecPython test mode | `2c7c:6002` | USB identity observed during testing | USB composite |

USB device numbers change after disconnects. Match by vendor/product ID and
physical port, then inspect the current device node. Never assume a prior
`/dev/bus/usb/BBB/DDD` path is still valid.

## AROM enumeration

The boot port was observed briefly after reset or power-up. Linux created a
`ttyACM` device, then the tracker disconnected and enumerated in its next mode.
Use a udev monitor or kernel log before triggering the transition so the short
window is visible. An AROM USB appearance alone does not mean the flash was
read or written.

## Access control

For persistent local access, a udev rule can grant a named local user access to
the specific USB IDs. Match the physical port where practical, reload rules,
then reconnect or retrigger the device. Keep permissions limited to the user
and required modes; do not use broad world-writable rules.

Example matching only the observed normal and AROM identities:

```udev
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", ATTR{idVendor}=="2ecc", ATTR{idProduct}=="3010", MODE="0660", GROUP="uucp"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", ATTR{idVendor}=="2ecc", ATTR{idProduct}=="3004", MODE="0660", GROUP="uucp"
```

Check your distribution's serial-device group and local udev policy before
installing. Add a serial match only if it is stable and non-sensitive.
