# Project 8: The Parallel Pizza Kitchen 🍕
*A POSIX-threaded order counter*

### The story
The pizza kitchen has several stations working at once. Each worker thread prepares part of the order count, but everyone shares the same tally board. Your job is to make the kitchen faster without letting concurrent updates corrupt the total.

### What you'll build
Build `parallel_pizzeria` with POSIX threads. Start multiple workers using `pthread_create()`, join them with `pthread_join()`, and compare an intentionally unsafe shared counter with a safe version protected by a mutex. Include a thread-unsafe function example and replace it with a thread-safe alternative or caller-owned storage.

### Sample output

```text
$ ./parallel_pizzeria
Workers: 4  Tasks per worker: 100000
Unsafe counter: 287413 (expected 400000; result may vary)
Safe counter:   400000 (expected 400000)
All workers joined. Kitchen closed.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| POSIX threads | Split the work among concurrently executing worker threads. |
| `pthread_create()` | Launch each worker with a clear argument structure and check the returned error code. |
| `pthread_join()` | Wait for each worker and collect its completion before freeing shared state. |
| Thread-unsafe vs thread-safe functions | Demonstrate why shared static state can race; use a reentrant alternative or protect shared state. |
| Synchronization | Use a mutex around the shared counter; `volatile` alone does not make a data race safe. |

### Levels

**🥉 Bronze: One Worker** — Create a few threads, print worker IDs, and join every thread.

**🥈 Silver: Race the Counter** — Run a shared counter test and then fix it with a mutex.

**🥇 Gold: Kitchen Supervisor** — Add a repeatable benchmark, error handling for thread creation, and a thread-safe replacement for a non-reentrant helper.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. Why can the unsafe counter be less than the expected value even though every worker increments it?
2. Remove the mutex from a test copy and run it several times. Why might the result change between runs?
3. Why must shared arguments and data remain valid until worker threads are finished?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
