# U04 · The IOS operating system

**Completion:** learner-reported on 5 November 2026. **Basis:** local course project and reviewed exercise material where available.


## Scenario and scope

An introductory IOS Packet Tracer project is available. Marcelo reported completing the course through 19.1 IGP on 5 November 2026, which includes this exercise. No separate exercise PDF, topology image or device-output screenshot was present alongside this particular `.pkt` file.

## Command walkthrough

| Command | Purpose | Prompt/context |
|---|---|---|
| `enable` | Enter privileged EXEC | `Router>` → `Router#` |
| `configure terminal` | Enter global configuration | `Router#` → `Router(config)#` |
| `hostname R1` | Set a device hostname | Global configuration |
| `interface gigabitEthernet 0/0` | Select the actual interface | Global configuration |
| `exit` | Return one configuration level | Configuration submode |
| `end` | Return to privileged EXEC | Configuration mode |
| `show running-config` | Inspect active configuration | EXEC |
| `copy running-config startup-config` | Save the intended IOS state | Privileged EXEC |

This is an original explanatory reference for the IOS topic, not a reconstruction of an unavailable course worksheet or a transcript from Marcelo's device. Use `?` and supported command completion to check available syntax.

## Troubleshooting and solution

When IOS rejects a command, inspect the prompt, caret position, spelling and available help before changing configuration. A command valid in privileged EXEC can fail in user EXEC or a configuration submode. Enter the appropriate mode, then retry only the intended command. [L01's save case](L01-access-port.md#case-2--configuration-save-rejected) contains actual captured evidence of this issue.

## Validation / rollback

Confirm the intended hostname and active settings with `show running-config`; save only after verification. Open a separate copy to practice. Completion is learner-reported; command output and final internal project state have not been independently checked.

[Packet Tracer project](../packet-tracer/U04-ios.pkt) · [Course attribution](../ATTRIBUTION.md) · [Command reference](../docs/COMMANDS.md) · [Index](../README.md)
