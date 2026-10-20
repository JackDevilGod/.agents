---
name: test-code
description: Run, test, and report errors in code files using execution only — never modifying the source.
disable-model-invocation: false
---

# Test Code

Execute the target file, capture output, and report errors — never edit any source.

## Rules
- Zero modification: never edit, patch, or touch any files.
- No self-correction: do not fix errors or failures.
- Capture STDOUT and STDERR.
- Report everything verbatim to the user.

## Workflow

### 1. Detect environment & command
Pick the compiler/interpreter for the file's language.

| Language / Extension | Runtime / Compiler | Preferred Test Command |
| :--- | :--- | :--- |
| **Python** (`.py`) | Python 3 | `python3 -m unittest` or `python3 <file>` |
| **JavaScript / TypeScript** (`.js`, `.ts`) | Node.js / `tsx` | `node <file>` or `npx tsx <file>` |
| **C / C++** (`.c`, `.cpp`) | `gcc` / `g++` | `gcc -Wall -Wextra -O0 <file> -o /tmp/out && /tmp/out` |
| **Rust** (`.rs`) | `rustc` | `rustc --crate-type bin <file> -o /tmp/out && /tmp/out` |
| **Go** (`.go`) | Go toolchain | `go run <file>` |
| **Java** (`.java`) | JDK | `javac <file> && java <class>` |

### 2. Generate synthetic test inputs
Feed edge-case inputs to break common paths:
- **Numeric**: `0`, `-1`, `MAX_INT`, `MIN_INT`, float edges (`NaN`, `Infinity`).
- **Strings**: `""`, single char, multi-byte UTF-8, 10,000+ chars, special chars (`\n`, `\0`, quotes).
- **Data structures**: `[]`, single element, null/nil, duplicate keys, deep nesting.
- **Control structures**: early returns, out-of-bounds index, division by zero.

### 3. Run & capture
Execute and capture STDOUT and STDERR.

### 4. Report results
Present output and errors verbatim.
