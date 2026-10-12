# Project 13: The Secret Recipe Courier 🔐
*Encrypting and authenticating a private message*

### The story
A courier carries a secret recipe between two friendly kitchens. You’re responsible for making sure only someone with the shared key can read it and that tampering is detectable. The project compares legacy algorithms with modern authenticated encryption rather than pretending every algorithm is equally safe.

### What you'll build
Build `recipe_lock` using a maintained cryptographic library. Demonstrate symmetric encryption and decryption with AES in an authenticated mode such as AES-GCM, plus a SHA-256 digest for comparison. If your course requires `crypt()` or RC4, isolate them in a clearly labeled legacy demonstration and explain their limitations; never use RC4 for new security work. `crypt()` is generally a password-hashing API, not a general-purpose reversible cipher.

### Sample output

```text
$ ./recipe_lock
Plaintext: add saffron after simmering
Cipher: AES-256-GCM
Encrypted bytes: 44
Decryption check: success
Tamper test: authentication failed (expected)
SHA-256 digest: 8f2a... (truncated for display)
Recipe delivered securely.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| AES | Encrypt and decrypt the message with a vetted library and an authenticated mode such as AES-GCM. |
| `crypt()` | If required by the course environment, demonstrate its password-hashing role separately; do not treat it as reversible message encryption. |
| RC4 | Include only as a legacy analysis/demo showing why obsolete stream ciphers should not protect new data. |
| SHA-256 | Compute a digest for integrity comparison; explain that a bare hash does not authenticate data. |
| Symmetric key encryption/decryption | Use the same secret key for both operations, with a fresh nonce/IV as required by the selected mode. |

### Levels

**🥉 Bronze: Lock and Unlock** — Encrypt and decrypt a message with a vetted library and confirm the recovered plaintext matches.

**🥈 Silver: Tamper Alarm** — Use authenticated encryption and deliberately alter the ciphertext to confirm decryption fails authentication.

**🥇 Gold: Security Courier** — Document key and nonce handling, compare a digest with a keyed MAC, and explain why the legacy demo is not suitable for production.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. What happens when you flip one bit of the authenticated ciphertext? Why is that different from merely decrypting and comparing a hash?
2. Why must a nonce/IV follow the requirements of the chosen AES mode, and why is nonce reuse dangerous for GCM?
3. Why are `crypt()` and RC4 not interchangeable with modern symmetric encryption?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
