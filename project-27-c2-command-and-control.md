# Project 27: The Local Fleet Dispatch Simulator 📡
*A loopback-only command-and-status exercise*

### The story
A fleet of toy robots reports status to a dispatch console. You’re writing both ends of the simulator on your own machine. The messages are fixed, harmless status commands—not a remote shell, payload delivery system, or third-party control channel.

### What you'll build
Build a loopback-only client/server simulator using a documented message allowlist such as `STATUS`, `PING`, and `STOP_SIMULATION`. Demonstrate datagram and stream message handling, and use `select()`, `poll()`, or `epoll` to monitor local sockets. Bind only to `127.0.0.1`; do not implement arbitrary command execution, persistence, stealth, or external connectivity.

### Sample output

```text
$ ./dispatch_server
Dispatch listening on 127.0.0.1:6060
Client #1 connected
Received: STATUS
Reply: STATUS=IDLE
Received: PING
Reply: PONG
Received: STOP_SIMULATION
Simulation stopped. 0 external peers accepted.
$ ./fleet_client
STATUS=IDLE
PONG
Simulation shutdown acknowledged
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| C2 (concept) | Model a benign controller and clients with a fixed, visible protocol and no arbitrary command execution. |
| `socket()` | Create the local TCP/UDP sockets required for the exercise. |
| `sendto()` / `recvfrom()` | Exchange a bounded UDP status datagram. |
| `bind()` / `listen()` / `accept()` | Create a loopback TCP listener and accept local clients. |
| `connect()` | Connect the local client to the simulator. |
| `select()` / `poll()` / `epoll` | Wait for activity on one or more local sockets; choose the API available on your platform. |

### Levels

**🥉 Bronze: One Robot** — Exchange a fixed status message over loopback TCP.

**🥈 Silver: Fleet Console** — Add UDP status packets and multiplex multiple local sockets with one supported polling API.

**🥇 Gold: Safety Dispatcher** — Add message validation, client limits, timeouts, and an audit log; prove the server rejects unknown commands and non-loopback binding.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. Send an unknown command to your local server. How does the allowlist handle it?
2. What happens if a client disconnects halfway through a TCP message? How does your framing logic recover?
3. Which design choices prevent this simulator from becoming an arbitrary remote command-execution tool?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
