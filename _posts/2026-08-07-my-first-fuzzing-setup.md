---
layout: post
title:  "My First Fuzzing Setup"
date:   2026-08-07
categories: fuzzing
---

I'm interested in fuzzing for bugs, so here's the stack I start every new
campaign with. Everything is open source and runs anywhere.

**Coverage-guided fuzzing with AFL++:**

```console
$ afl-gcc-fast -fsanitize=address -o target target.c
$ afl-fuzz -i seeds/ -o out/ -- ./target @@
```

The `@@` means the file input goes in place of a filename argument. ASan makes
sure we catch memory corruption instead of silent crashes.

**Why coverage-guided works:** the fuzzer keeps every input that reaches new
code, then mutates and recombines them. Over time it explores deeper code
paths than pure mutation ever could.

Start with a small corpus of valid inputs — the fuzzer does the rest.
