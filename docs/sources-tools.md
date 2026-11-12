# Research sources and tools

## Hardware and firmware references

- [FoxExe/ZX908](https://github.com/FoxExe/ZX908) — related tracker project and
  firmware/application reference. Similarity to ZX909 is not proof of hardware
  or firmware compatibility.
- [QuecPython Thonny plugin](https://github.com/QuecPython/thonny-quecpython) —
  host integration reference; does not establish that this tracker supports
  QuecPython.
- [Quectel QDL Linux guide](https://developer.quectel.com/doc/sbc/Quectel-Pi-H1/en/OS/Debian/system_flash.html)
  — useful comparison for Quectel Pi H1, but a different chipset/download path.
- [Linux QDL](https://github.com/linux-msm/qdl) — Qualcomm Sahara/Firehose
  tooling; not the ASR AROM protocol used by this tracker.

## Tools used during investigation

- Linux kernel USB logs, `lsusb`, udev, and CDC ACM for enumeration and serial
  access.
- Quectel QDloader Linux Android V1.2.0 with an AROM-compatible release package
  for the original-image restore.
- `qmicli` on a separate Qualcomm USB modem as a local LTE reference.
- REA and Ghidra for firmware extraction and static inspection.
- `binwalk` for firmware signature and region triage.
- Git and plain-text timestamped evidence records for changes and observations.

Keep tool versions, command lines, and sanitized logs with each experiment.
This public repository intentionally excludes binary dumps, private device
identifiers, local file paths, and credentials.
