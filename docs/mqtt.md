# MQTT development path

The target goal is a tracker that can be configured over USB and publish useful
telemetry over MQTT. This has not yet been demonstrated on the device.

## Staged plan

1. Restore and preserve the original firmware.
2. Establish reliable SIM readiness, LTE registration, and packet data.
3. Identify which modem firmware and AT interface are active.
4. Verify whether the matching QuecPython runtime is supported by this exact
   module, then run a minimal local script before attempting networking.
5. Add USB configuration and status commands for APN, MQTT host, port, TLS,
   credentials, publish interval, signal, GPS, and device state.
6. Add MQTT connect/publish/reconnect behavior and validate it against a
   controlled broker.

Each stage should have a rollback image and a narrow check. Keep broker
addresses, account names, passwords, certificates, and device identities in
private local configuration; never commit them to source control.

The original firmware includes cellular and tracker control strings, but the
presence of strings does not prove a command is supported or safe. Test only
documented or previously observed commands and preserve responses with private
identifiers redacted.
