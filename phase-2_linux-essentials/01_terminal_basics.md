# 01 — Terminal Basics

---

## Scenario

As part of Phase 2 in building a secure and operational Linux lab, I focused on mastering the Linux terminal. This module covered foundational command-line skills needed to navigate the file system, manipulate files, understand input/output redirection, and combine commands effectively. These are critical daily skills for SOC analysts and system administrators who rely on speed, precision, and automation when working in Unix-like environments.

---

## What I Did

- Verified shell type using:
  ```bash
  echo $SHELL
  ```
- Practiced directory navigation:
  ```bash
  pwd
  ls -lAh
  cd /etc
  cd ~
  cd ..
  ```
- Created and manipulated files:
  ```bash
  mkdir demo_dir
  touch demo_dir/file1.txt
  echo "hello world" > demo_dir/file1.txt
  cp demo_dir/file1.txt demo_dir/file2.txt
  mv demo_dir/file2.txt demo_dir/renamed.txt
  rm demo_dir/renamed.txt
  rmdir demo_dir
  ```
- Viewed and edited files with:
  ```bash
  cat /etc/hosts
  less /etc/passwd
  nano ~/.zshrc
  ```
- Used built-in help:
  ```bash
  man ls
  ls --help
  ```
- Practiced redirection and piping:
  ```bash
  echo "first line" > test.txt
  echo "second line" >> test.txt
  cat < test.txt
  cat test.txt | grep "first"
  ```
- Practiced command chaining:
  ```bash
  mkdir test && cd test
  cd /nope || echo "Failed!"
  cd ~; ls
  ```

---

## What I Learned

- The distinction between terminal emulators and shells (Zsh vs Bash)
- How to confidently navigate and manage the Linux filesystem via command-line
- The mechanics of input/output redirection (`>`, `>>`, `<`) and how they control streams
- How piping (`|`) can combine simple tools into powerful data workflows
- Command chaining with `&&`, `||`, and `;` enables conditional or sequential execution
- That `man` and `--help` are essential tools for self-guided discovery and troubleshooting

---

## Why It Matters

Mastery of the terminal is a prerequisite for nearly every role in cybersecurity and system administration. Whether reviewing logs, automating scripts, or deploying tools in a remote environment, the terminal provides unmatched efficiency and control. Building this foundation prepares me to confidently approach more advanced topics in Linux-based defensive operations.

---

