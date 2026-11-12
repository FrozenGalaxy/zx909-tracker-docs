# AT command notes

These commands were used with the original tracker firmware. Support and exact
responses can vary by firmware revision. Capture a baseline before changing
anything and redact subscriber/device identifiers from logs.

## Useful read-only queries

| Purpose | Command |
|---|---|
| SIM readiness | `AT+CPIN?` |
| Signal quality | `AT+CSQ` |
| Extended signal | `AT+CESQ` |
| LTE registration | `AT+CEREG?` |
| Packet attach | `AT+CGATT?` |
| Operator selection | `AT+COPS?` |
| PDP contexts | `AT+CGDCONT?` |
| Device identity | `AT+CGSN` |
| Reset | `AT+RESET` |

The last command changes device state. Query commands may still reveal private
identifiers; redact their output before sharing.

## Observed LTE interpretation

On the latest original-firmware boot, the SIM was ready and the modem reported
signal, but registration was limited (`CEREG` status 3 / rejection-related
state) and `CGATT` remained 0. A later cell report showed O2 `26203` in limited
service, with substantially weaker received power than the separate reference
modem. The evidence does not isolate firmware from RF or calibration causes.

## Changes and locks

Network selection, band locks, and undocumented vendor commands can cause
re-enumeration or loss of service. Record the original setting and restore
automatic selection after a test. Avoid copying undocumented commands from
another chipset without confirming they apply to this firmware.
