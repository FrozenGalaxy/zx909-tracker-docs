# LTE findings

## Local reference network

A phone and an independent Qualcomm USB modem both observed O2 Germany on
PLMN `26203` near the tracker test location. The phone showed LTE bands 1, 3,
and 20; the strongest displayed serving cell was band 3, EARFCN 1600. The
reference modem registered and attached successfully on O2. Exact cell IDs,
TAC, PCI, and coordinates are omitted from this public record.

This confirms that O2 service was available to those devices at the test time.
The SIMs and radios were different, so it does not rule out tracker-SIM policy
or device compatibility issues.

## Tracker results

The tracker has previously worked on LTE with its original firmware according
to the owner. After a full original-image restore, it booted normally, reported
`CSQ 16`, and showed LTE signal, but did not register normally on O2 or attach
for data. Manual tests on locally covered bands 1 and 3 could see O2 in limited
service, but did not establish packet attachment. Reported RSRP was weaker than
the reference modem; the tracker uses a small integrated PCB antenna.

## Current conclusion

The evidence does **not** prove that modem firmware is broken. It points to a
tracker-specific problem. Plausible causes include modem firmware/configuration,
NVM calibration, RF path or antenna performance, band configuration, and
device/SIM policy. Signal checks should be recorded alongside registration and
attach state, since weak RF could contribute but is not established as the sole
cause.

## Next useful checks

- Capture `CPIN`, `CSQ`, `CESQ`, `CEREG`, `CGATT`, `COPS`, and PDP context state
  in one timestamped snapshot.
- Compare automatic selection and the same confirmed O2 band while monitoring
  serving-cell and signal data.
- Inspect original modem firmware and NVM/calibration regions before changing
  them; preserve the original image.
- Avoid a full flash readback during ordinary application iteration. Reserve it
  for backup or explicit verification.
