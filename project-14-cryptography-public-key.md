# Project 14: The Royal Key Exchange 🗝️
*A public-key identity and digest lab*

### The story
Two kingdoms want to exchange a message without first sharing a secret key. You’re the royal cryptographer: create a key pair, protect a short message, verify who signed it, and compare hash algorithms of different generations.

### What you'll build
Build `royal_keys` with a maintained cryptographic library. Generate an RSA key pair, encrypt a short message using an appropriate modern RSA padding scheme (or use RSA to wrap a randomly generated symmetric key), and sign/verify a message. Calculate MD5, SHA-1, and SHA-512 digests for comparison, clearly labeling MD5 and SHA-1 as unsuitable for modern collision-resistant security uses.

### Sample output

```text
$ ./royal_keys
RSA key pair created (demo key)
Message encrypted with RSA-OAEP.
Private-key decryption: success
Signature verification: valid
MD5:    5d41... (legacy comparison)
SHA-1:  7c21... (legacy comparison)
SHA-512: a9b3... (truncated)
Royal dispatch verified.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| RSA | Generate and use an RSA key pair through a cryptographic library, with suitable key sizes and padding. |
| MD5 / SHA-1 / SHA-512 | Compare digest outputs; label MD5 and SHA-1 as legacy and collision-broken for security-sensitive integrity use. |
| Public and private keys | Use the public key for appropriate encryption/verification operations and the private key for decryption/signing; do not confuse the roles. |

### Levels

**🥉 Bronze: Create the Keys** — Generate a key pair and display public-key metadata without printing private key material.

**🥈 Silver: Encrypt and Verify** — Encrypt/decrypt a short message and sign/verify a message with safe library defaults.

**🥇 Gold: Royal Auditor** — Tamper with a signed message, show verification fails, and compare digest algorithms while documenting why hybrid encryption is used for larger data.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. What happens when you verify a signature after changing one byte of the signed message?
2. Why is RSA generally not used to encrypt a large file directly?
3. Why should MD5 and SHA-1 appear only as historical comparisons in this project?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
