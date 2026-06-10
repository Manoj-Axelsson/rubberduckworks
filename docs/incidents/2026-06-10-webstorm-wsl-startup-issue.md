# Incident Report

## Metadata

| Field | Value |
|----------|-----------------------------|
| Date | 2026-06-10 |
| Project | RubberDuckWorks |
| Severity | Medium |
| Status | Workaround Available |
| Reporter | Manoj Axelsson |
| External Issue | WEB-78351 |
| JetBrains Platform Issue | IJPL-236844 |

---

# Summary

WebStorm 2026.1.2 hangs indefinitely on the splash screen when attempting to open a WSL project.

The problem was reproduced consistently and isolated to the WSL startup path.

---

# Environment

- Windows 11
- Ubuntu WSL
- WebStorm 2026.1.2
- Windows PowerShell 5.1

Project location:

```
\\wsl.localhost\Ubuntu\home\manoj_axelsson\projects\rubberduckworks
```

---

# Symptoms

- Splash screen never disappears.
- CPU usage remains low.
- Memory usage remains stable.
- Project never opens.

Eventually:

```
java.lang.NullPointerException

Cannot invoke
java.io.FileDescriptor.closeAll(java.io.Closeable)

because "this.fd" is null
```

---

# Investigation Timeline

## Initial assumptions

- WebStorm installation corrupted
- WSL path invalid
- PowerShell launcher incorrect

Result:

Not confirmed.

---

## Experiments

### Direct executable

Result:

Works.

---

### PowerShell

Result:

Works.

---

### WSL launcher

Result:

Hangs.

---

### Stack trace analysis

Observed:

```
WslIjentAvailabilityService

EelWslMrfsBackend
```

---

### JetBrains YouTrack

Created:

WEB-78351

Response:

Linked to:

IJPL-236844

---

# Root Cause

Likely IntelliJ Platform WSL/IJent startup issue.

Not caused by:

- Project
- WSL installation
- PowerShell
- Launcher scr
# Workaround

Close all JetBrains IDEs.

Rename:

```
recentProjects.xml
```

to

```
recentProjects.xml.bak
```

Restart WebStorm.

Open the project manually from the Welcome Screen.

---

# Lessons Learned

- Debug one variable at a time.
- Preserve evidence instead of deleting files.
- Create reproducible cases before reporting bugs.
- Report stack traces and environment information.
- Workarounds should be reversible whenever possible.

---

# References

WEB-78351

IJPL-236844