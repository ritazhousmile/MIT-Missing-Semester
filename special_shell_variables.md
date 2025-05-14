
# 💡 Special Shell Variables Cheat Sheet

These are special variables used in `bash`, `zsh`, and other POSIX-compatible shells.

---

## 🔢 Positional Parameters

| Variable | Meaning                                  |
|----------|------------------------------------------|
| `$0`     | Name of the script itself                |
| `$1`, `$2`, ... | First, second, etc. arguments to the script |
| `$#`     | Number of arguments passed to the script |
| `$@`     | All arguments (as separate quoted words) |
| `$*`     | All arguments (as a single word)         |

---

## 🔁 Exit Status and Process

| Variable | Meaning                                       |
|----------|-----------------------------------------------|
| `$?`     | Exit status of the **last command**           |
| `$$`     | Process ID (PID) of the **current shell**     |
| `$!`     | PID of the **last background command**        |

---

## 🔐 Quotes: `$@` vs `$*`

| Context         | Behavior                            |
|----------------|--------------------------------------|
| `"$@"`         | Preserves each argument as-is        |
| `"$*"`         | Joins all arguments into one string  |

**Example:**
```bash
./script.sh one "two three"
```

| Variable  | Expands to                          |
|-----------|-------------------------------------|
| `"$@"`    | `"one"` `"two three"` (2 elements)  |
| `"$*"`    | `"one two three"` (1 element)       |

---

## 📋 Script Example

```bash
#!/bin/bash
echo "Script name: $0"
echo "First arg: $1"
echo "All args: $@"
echo "Number of args: $#"
```

Run with:
```bash
bash test.sh hello world
```

Output:
```
Script name: test.sh
First arg: hello
All args: hello world
Number of args: 2
```

---

## 🧠 Summary

| Symbol | Meaning                              |
|--------|---------------------------------------|
| `$0`   | Script name                          |
| `$1`   | First argument                       |
| `$#`   | Argument count                       |
| `$@`   | All arguments (individually quoted)  |
| `$*`   | All arguments (single word)          |
| `$?`   | Last command's exit status           |
| `$$`   | Current shell's process ID           |
| `$!`   | Last background process ID           |

---
