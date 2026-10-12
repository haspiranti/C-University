# Project 24: The Windows Service Garage 🔧
*Managing a disposable demonstration service*

### The story
A maintenance garage needs to understand the Windows Service Control Manager (SCM) lifecycle. You’re the service mechanic, working only with a clearly named service that you create for this lab and can remove afterward.

### What you'll build
Build a Windows service demo with a harmless service executable that logs lifecycle events and does no privileged work. A separate controller should use the SCM APIs to create, open, start, stop, reconfigure, and delete only the lab service. Require explicit confirmation before destructive actions, check every API result, and clean up the service at the end.

### Sample output

```text
C:\Lab> service_garage.exe install
SCM opened.
Created service: CProjectLabDemo
Start requested: success
Service state: RUNNING
Stop requested: success
Service state: STOPPED
Lab service deleted. Garage closed.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| SCManager | Open the Service Control Manager with the minimum required access. |
| `CreateService()` | Create a uniquely named, harmless lab service with a known executable path. |
| `StartService()` | Start the lab service and inspect its state. |
| `StopService()` | Request a stop and wait for the service to reach the stopped state. |
| `DeleteService()` | Delete only the lab service after it has been stopped; remember deletion may be pending until handles close. |
| `OpenService()` | Open the named lab service with the specific rights needed for an operation. |
| `ChangeServiceConfig()` | Change a harmless lab setting such as display name or start type, then restore the original lab configuration. |

### Levels

**🥉 Bronze: Garage Door** — Build a service that starts, logs a message, and stops cleanly.

**🥈 Silver: Full Service Cycle** — Add controller commands for create/open/start/stop/delete with state checks.

**🥇 Gold: Safe Mechanic** — Add configuration changes, explicit confirmation, robust rollback, and a cleanup check proving the lab service is gone.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. What happens if you call `DeleteService()` while the service is still running or a handle remains open?
2. Try starting a service with an invalid executable path. Which API reports the failure?
3. Why should service creation and reconfiguration require least privilege and explicit confirmation?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
