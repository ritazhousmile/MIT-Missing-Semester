
# 🐚 Shell Command Cheat Sheet (Beginner Essentials)

## 📁 Navigation
| Action                    | Command               |
|---------------------------|------------------------|
| Show current directory    | `pwd`                 |
| List files                | `ls`                  |
| List with details         | `ls -l`               |
| Go into directory         | `cd foldername`       |
| Go up one level           | `cd ..`               |
| Go to home directory      | `cd ~` or just `cd`   |
| Clear screen              | `clear`               |

## 🗂️ Files and Folders
| Action                        | Command                     |
|-------------------------------|------------------------------|
| Create a new file             | `touch filename.txt`        |
| Create a new folder           | `mkdir foldername`          |
| Delete a file                 | `rm filename.txt`           |
| Delete a folder (recursive)   | `rm -r foldername`          |
| Move or rename a file/folder  | `mv oldname newname`        |
| Copy a file                   | `cp file1.txt file2.txt`    |
| Copy folder recursively       | `cp -r folder1 folder2`     |

## 📝 Viewing File Content
| Action                 | Command                  |
|------------------------|---------------------------|
| Show full content      | `cat filename`           |
| Scroll file            | `less filename`          |
| Head (first 10 lines)  | `head filename`          |
| Tail (last 10 lines)   | `tail filename`          |
| Real-time log view     | `tail -f filename`       |

## 🔍 Searching & Finding
| Action                        | Command                                |
|-------------------------------|-----------------------------------------|
| Search text in file           | `grep "text" filename`                |
| Case-insensitive search       | `grep -i "text" filename`             |
| Find files by name            | `find . -name "filename"`             |
| Find text recursively         | `grep -r "text" directory/`           |

## 🛠️ System Info & Management
| Action                  | Command              |
|-------------------------|-----------------------|
| Show current user       | `whoami`             |
| Show date/time          | `date`               |
| Show running processes  | `ps` or `top`        |
| Show disk usage         | `df -h`              |
| Show memory usage       | `free -h`            |

## 🔄 Permissions & Executables
| Action                        | Command                        |
|-------------------------------|---------------------------------|
| Make file executable          | `chmod +x filename.sh`         |
| Change file permissions       | `chmod 755 filename`           |
| Change file owner             | `chown user:group filename`    |

## 🧪 Running Scripts
| Action                         | Command              |
|--------------------------------|-----------------------|
| Run a shell script             | `bash script.sh`      |
| Run with current shell         | `./script.sh`         |

---

## 🚀 Bonus Tips
- Use `Tab` for auto-completion.
- Use `Ctrl + C` to stop a running process.
- Use `history` to see past commands.
- Use `!!` to repeat the last command.

---
