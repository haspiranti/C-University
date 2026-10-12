# Project 7: The Two-Ship Radio Challenge 🚢
*A local TCP and UDP message exchange*

### The story
Two ships in a training harbor need to exchange messages. You’re building their radio consoles: one connection-oriented TCP channel for reliable conversations and one UDP channel for short datagrams. Everything runs on your own computer.

### What you'll build
Build a local client/server demo with a TCP greeting and a UDP status packet. Bind only to loopback (`127.0.0.1`), use a fixed documented port, validate input, and handle socket errors. Show the TCP server accepting a client and the UDP receiver handling one datagram; do not expose the demo to external interfaces.

### Sample output

```text
$ ./radio_server
TCP listening on 127.0.0.1:5055
UDP ready on 127.0.0.1:5056
TCP client connected
TCP received: READY
UDP received: STATUS: green
Server shutting down
$ ./radio_client
Connected to local harbor
TCP reply: AHOY
UDP status sent
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| `socket()` | Create TCP (`SOCK_STREAM`) and UDP (`SOCK_DGRAM`) sockets. |
| `bind()` | Attach server sockets to loopback addresses and the chosen local ports. |
| `listen()` | Place the TCP listening socket into passive mode. |
| `accept()` | Accept a TCP client and use the returned connected socket for that conversation. |
| `connect()` | Connect the TCP client to the loopback server. |
| `send()` / `recv()` | Exchange TCP bytes; account for partial sends/receives and stream framing. |
| `inet_pton()` | Convert the numeric loopback address into the binary address representation. |
| TCP vs UDP | Demonstrate a TCP stream exchange and a UDP datagram exchange; UDP does not guarantee delivery or ordering. |

### Levels

**🥉 Bronze: TCP Handshake** — Run a loopback TCP server and client that exchange one short message.

**🥈 Silver: Harbor Radio** — Add UDP status messages and handle errors, partial TCP reads, and orderly socket closure.

**🥇 Gold: Radio Engineer** — Add message framing, timeouts, and a small test that demonstrates UDP loss or TCP stream chunking without using any external host.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. Why can one `recv()` call return fewer bytes than the sender passed to `send()`?
2. Send an empty or malformed message to your local server. What happens, and how do you handle it?
3. Compare TCP and UDP based on what your program actually observed, not just their API names.

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
