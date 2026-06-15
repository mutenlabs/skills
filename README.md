# MUTEN Skills

Public skill packages for the Mu runtime.

Each package lives under `skills/<id>/` and follows the
[Agent Skills](https://agentskills.io) directory format:

```text
skills/<id>/
  SKILL.md
  references/
  scripts/
  assets/
```

`SKILL.md` is required. The other directories are optional. Script files are
distributed as package assets; Mu script execution is not part of the first
runtime release.

## Registry

[`registry.json`](registry.json) is the machine-readable marketplace index.
Every entry declares package metadata and an explicit file list:

```json
{
  "id": "example",
  "name": "Example",
  "description": "Describe when the agent should use this skill.",
  "version": "1.0.0",
  "platform": "esp32",
  "checksum": "optional package checksum",
  "files": [
    {
      "path": "SKILL.md",
      "url": "https://mutenlabs.github.io/skills/skills/example/SKILL.md",
      "sha256": "required for published files",
      "size": 1234
    }
  ]
}
```

`platform` is optional. When omitted, the package is portable. When present,
it must match Mu's platform identifier, such as `esp32` or `desktop`; Mu marks
the package incompatible on other platforms.

Published file entries should include a SHA-256 checksum and byte size. Mu
downloads every file transactionally and rejects per-file checksum failures.
