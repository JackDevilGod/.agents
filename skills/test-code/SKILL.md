---
name: test-code
description: Run, test, and report errors in code files using execution only — never modifying the source.
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

| Language | Runtime | Command |
| :--- | --- | :--- |
| **Python** | Python 3 | `python3 -m unittest` or `python3 <file>` |
| JavaScript/TypeScript | Node.js | `node <file>` or `npx tsx <file>` |
| C/C++ | gcc/g++ | `gcc -Wall -Wextra -O0 <file> -o /tmp/out && /tmp/out` |
| Rust | rustc | `rustc --crate-type bin <file> -o /tmp/out && /tmp/out` |
| Go | Go | `go run <file>` |
| Java | JDK | `javac <file> && java <class>` |

### 2. Generate synthetic test inputs
Feed edge-case inputs to break common paths:
- **Numeric**: `0`, `-1`, `MAX_INT`, `MIN_INT`, `NaN`, `Infinity` (JS/Python)
- **Strings**: empty (`""`), single char, 10K+ chars, special (`\n`, `\0`, quotes, unicode)
- **Data structures**: `[]`, `[null]`, deep nesting, duplicate keys
- **Control flow**: early returns, empty branches, division by zero, unhandled exceptions

### 3. Run & capture
Execute and capture STDOUT and STDERR.

### 4. Report results
Present output and errors verbatim.
