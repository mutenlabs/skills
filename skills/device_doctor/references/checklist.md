# Device Doctor Checklist

Use this checklist only when the initial facts are not enough for a confident diagnosis.

## Connection

1. Confirm the device is powered and connected to the expected network.
2. Confirm the device is attached to the expected account.
3. Confirm the gateway or broker connection is healthy.
4. Check whether Console has received a recent system or hardware report.

## Runtime

1. Check the platform identifier, firmware version, and recent restart history when available.
2. Look for recent configuration changes, provider changes, or credential changes.
3. Confirm the current model provider exposes the same tool surface as expected.

## Skills

1. Use `list_installed_skills` to separate local installed skills from remote marketplace skills.
2. Confirm the expected skill id is installed locally.
3. Confirm the skill is activated in the current session when its instructions are needed.
4. Use `read_skill_file` to inspect supporting files when the skill references them.
5. Check platform compatibility metadata before assuming a package is broken.
6. Check for partial installs, checksum failures, or missing files if installation failed.

## Tools

1. Confirm the tool exists in the current tool inventory or provider tool list.
2. Confirm the tool name matches the user's intent.
3. Check for permission, approval, or capability errors before changing code.
4. Separate model confusion from runtime failure: a tool can exist even if the model did not choose it.

## Hardware

1. Confirm the required platform or hardware matches the current device.
2. Confirm required peripherals are present before running hardware-specific workflows.
3. Avoid recommending firmware or wiring changes unless the evidence points there.

## Final Answer

Prefer a short diagnosis with an ordered checklist. The user should leave with the next
two or three actions, not a wall of possibilities.
