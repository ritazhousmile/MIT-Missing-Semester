
# 📝 Vim Cheat Sheet (Beginner Essentials)

- vim stands for Vi IMproved — it’s a powerful, efficient text editor used mainly in command-line environments like Linux and macOS terminals.

#🔹 What is vim?
- It’s an enhanced version of the classic vi editor, offering more features like syntax highlighting, undo/redo, better search, plugins, etc.
- It’s keyboard-driven: most operations (editing, saving, searching) are done using commands, not menus or buttons.
- It’s popular among programmers and sysadmins for editing code, scripts, and config files directly from the terminal.

#  Why use vim?
- It’s lightweight and pre-installed on most Unix systems.
- Ideal for remote servers where no GUI is available.
- Extremely powerful once you learn it — supports macros, plugins, code linting, etc.


## ✍️ Insert Mode
| Action                     | Key         |
|----------------------------|-------------|
| Start typing before cursor | `i`         |
| Start typing after cursor  | `a`         |
| Insert on new line below   | `o`         |
| Exit Insert mode           | `Esc`       |

## 🧭 Moving Around (Normal Mode)
| Action                  | Key           |
|-------------------------|----------------|
| Left / Down / Up / Right | `h` / `j` / `k` / `l` |
| Start of line           | `0`           |
| End of line             | `$`           |
| Next word               | `w`           |
| Previous word           | `b`           |
| Go to line N            | `:N` (e.g., `:10`) |

## 🧹 Editing Text (Normal Mode)
| Action                  | Key           |
|-------------------------|----------------|
| Delete character        | `x`           |
| Delete line             | `dd`          |
| Undo                    | `u`           |
| Redo                    | `Ctrl + r`    |
| Copy line               | `yy`          |
| Paste                   | `p`           |

## 💾 File Commands (Command Mode - type `:` first)
| Action              | Command      |
|---------------------|---------------|
| Save                | `:w`          |
| Quit                | `:q`          |
| Save and Quit       | `:wq` or `ZZ` |
| Quit without saving | `:q!`         |

---

## 🚀 Quick Start Tutorial

1. Open a file:
    ```bash
    vim test.txt
    ```

2. Enter Insert mode:  
   Press `i` and start typing.

3. Exit Insert mode:  
   Press `Esc`.

4. Save and quit:
    ```vim
    :wq
    ```

---


Run this in your terminal:
```bash
vimtutor
```

