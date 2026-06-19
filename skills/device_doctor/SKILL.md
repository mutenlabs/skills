---
{
  "name": "device_doctor",
  "description": "Diagnose Mu device issues and produce a concise troubleshooting report with likely causes and next checks.",
  "author": "MUTEN",
  "metadata": {
    "category": ["utility", "debugging"],
    "tags": ["mu", "device", "skills", "tools", "troubleshooting"]
  }
}
---

# Device Doctor

Use this skill when the user says a Mu device is broken, offline, behaving strangely,
failing to connect, failing to install or activate a skill, or not running an expected
tool correctly.

## When To Use

- A device is offline, missing from Console, or failing to attach.
- A skill is installed but does not appear, activate, or behave as expected.
- A tool is missing, denied, incompatible, or returning unexpected results.
- The user wants a focused diagnosis before changing code, firmware, or hardware.

## Hard Rules

1. Do not invent device, firmware, network, storage, skill, or tool state.
2. Prefer facts from available context, inventory reports, and tools over guesses.
3. If `list_installed_skills` is available and the issue involves skills, call it before diagnosing.
4. If marketplace discovery is relevant, use `search_marketplace_skills` only for remote marketplace results.
5. If the issue needs a deeper checklist, call `read_skill_file` for `references/checklist.md`.
6. Ask for missing information only when it changes the diagnosis.
7. Keep fixes concrete and ordered from lowest risk to highest risk.

## Workflow

1. Restate the symptom in one sentence.
2. Capture known facts from the prompt and available tool results.
3. Identify unknowns that block a confident diagnosis.
4. List the most likely causes, with the evidence for each.
5. Provide next checks in the order the user should run them.
6. End with the smallest reasonable fix or experiment.

## Report Format

```text
Symptom:
Known facts:
Unknowns:
Most likely causes:
Next checks:
Suggested fix:
```

## Notes

For skill-store issues, explicitly distinguish:

- Local installed skills from `list_installed_skills`.
- Remote marketplace skills from `search_marketplace_skills`.
- Session activation state from installation state.
- Platform incompatibility from a failed download or missing package file.
