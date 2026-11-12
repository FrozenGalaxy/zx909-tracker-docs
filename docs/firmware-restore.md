# Firmware backup and restore

## What is known

The device was identified as an ASR AROM 0.6 platform with boot ROM dated
2022-11-06 and a 4 MiB QSPI flash. The original full flash image is stored
privately with the research files and is not distributed here. A full original
image was written back through the AROM/QDloader path; the tracker subsequently
booted into its original AT firmware.

The latest write was **not readback-verified byte-for-byte**. It is confirmed by
successful normal-mode enumeration and original-firmware AT responses. A prior
readback does not verify the latest write. Keep these claims distinct.

## Safe workflow

1. Identify the exact board, boot ROM, flash type, and capacity.
2. Preserve the complete original image and calculate a local cryptographic
   hash. Keep it off the public repository.
3. Confirm the host tool's documented target format and address range.
4. Capture the current AT and USB state.
5. Write only an image intended for that exact device.
6. Wait for the tool's completion result and normal USB re-enumeration.
7. Confirm boot with harmless AT queries. Perform readback only when an actual
   byte-for-byte verification is needed and the time is available.

Do not infer write completion from a partial progress line, or infer a complete
backup from an AT memory dump. An AT dump may cover only selected regions and
may omit modem/NVM data.

## Tool references

The research used Quectel QDloader Linux Android V1.2.0 and a locally built
AROM release package. These tools are vendor- and platform-specific; inspect
their instructions and logs before use. Qualcomm `qdl`/EDL packages target a
different download protocol and are not interchangeable with AROM.

Original firmware and tool binaries are excluded from this public project.
