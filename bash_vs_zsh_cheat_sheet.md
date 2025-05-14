
# 🆚 Bash vs Zsh: Comparison Cheat Sheet

## 🔍 Overview

Both **Bash** and **Zsh** are powerful Unix shells that provide a command-line interface to interact with the operating system. While they share many similarities, they also have distinct features.

---

## 📊 Feature Comparison

| Feature/Aspect            | `bash` (Bourne Again Shell)          | `zsh` (Z Shell)                          |
|---------------------------|--------------------------------------|------------------------------------------|
| 📦 Default Shell on       | Most Linux distros                   | macOS (since Catalina), some users       |
| 🧠 Script compatibility   | Standard; widely used in scripts     | Mostly compatible with `bash` scripts    |
| ⌨️ Auto-completion        | Basic                                | Advanced (smart tab completion)          |
| 🧲 Command suggestions    | No                                   | Yes (with plugins like `zsh-autosuggestions`) |
| 🎨 Themes & customization | Minimal                              | Excellent (with tools like `oh-my-zsh`)  |
| 📁 Path expansion         | Basic                                | Smarter globbing and expansion           |
| 🔄 Plugin support         | Manual                               | Built-in framework support (`oh-my-zsh`) |
| 🐚 Community use          | Most scripting tasks                 | Preferred by power users and devs        |

---

## 🌟 Notable Features in `zsh` (Not in `bash` by Default)

- ✅ Auto-suggestions as you type
- ✅ Command correction (`cd /documnts` → `cd /Documents`)
- ✅ Shared history between terminal tabs
- ✅ Recursive globbing (`ls **/*.txt`)
- ✅ Prompt customization with themes via `oh-my-zsh`

---

## 📜 Script Compatibility

- Bash is the standard for scripting; most scripts use `#!/bin/bash`.
- Zsh supports most Bash scripts, but edge cases may differ.
- For scripting: **Bash is safer** for portability.

---

## 💡 Recommendations

| You want...                          | Use...     |
|--------------------------------------|------------|
| Writing or running scripts reliably  | `bash`     |
| A powerful, user-friendly shell      | `zsh` + `oh-my-zsh` |
| Auto-completion and suggestions      | `zsh`      |
| Something already installed on Linux | `bash`     |
| A modern CLI environment on macOS    | `zsh` (default) |

---

## 🛠️ Install & Setup Zsh with `oh-my-zsh`

```bash
# Install Zsh (if not already installed)
sudo apt install zsh    # Debian/Ubuntu
brew install zsh        # macOS with Homebrew

# Set Zsh as your default shell
chsh -s $(which zsh)

# Install oh-my-zsh for themes and plugins
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

---

## 🔗 Further Reading

- [Bash Manual](https://www.gnu.org/software/bash/manual/)
- [Zsh Guide](https://zsh.sourceforge.io/Guide/zshguide.html)
- [Oh My Zsh](https://ohmyz.sh/)

---
