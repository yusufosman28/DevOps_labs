# Bash Scripting

![Script](https://img.shields.io/badge/Script-Bash-4EAA25?logo=gnubash&logoColor=white)
![OS](https://img.shields.io/badge/OS-Linux-blue?logo=linux)
![Focus](https://img.shields.io/badge/Focus-Automation-purple)
![Practice](https://img.shields.io/badge/Practice-Hands--on-orange)

This folder documents my hands-on learning of **Bash scripting**, from writing a first script to handling bad input and failing safely, followed by real problems I hit and how I worked through them.

Bash is how Linux commands become automation. Deployment steps, health checks, backups and CI/CD jobs are often Bash scripts, so writing scripts that behave predictably is a core DevOps skill.

My focus has been on **understanding why scripts behave the way they do**, especially the cases where Bash fails silently.

---

## Learning Objectives

Through this module, I aimed to:

- Write, permission and run scripts correctly
- Use variables, arrays, quoting and parameters
- Make decisions with conditionals and file tests
- Repeat work with `for` and `while` loops
- Organise code into functions and take user input
- Validate input and report failure with exit codes
- Make scripts fail loudly using `set -euo pipefail`
- Work with environment variables and `PATH`

---

## Topics Covered

### Fundamentals

- [Script Basics](./fundamentals/01-script-basics.md)  
  The shebang, execute permission, `./` vs `bash`, comments, and running scripts from anywhere.

- [Variables and Quoting](./fundamentals/02-variables-and-quoting.md)  
  Variables, single vs double quotes, interpolation and arrays.

- [Parameters and User Input](./fundamentals/03-parameters-and-input.md)  
  `$1`, `$@`, `$#`, `$0` and reading input with `read`.

- [Arithmetic and Command Substitution](./fundamentals/04-arithmetic.md)  
  `$(( ))` for maths and `$( )` for command output.

- [Conditionals](./fundamentals/05-conditionals.md)  
  `if`, `elif`, `else`, comparison operators and file tests.

- [Loops](./fundamentals/06-loops.md)  
  `for` and `while` loops, `break` and `continue`.

- [Functions](./fundamentals/07-functions.md)  
  Defining and calling functions, `local` variables and validating input.

- [Exit Codes and Error Handling](./fundamentals/08-exit-codes-and-error-handling.md)  
  `$?`, `exit` vs `return`, and the `set` safety options.

- [Environment Variables and PATH](./fundamentals/09-environment-and-path.md)  
  System variables and making `PATH` changes permanent.

---

### Troubleshooting

- [What Broke and How I Fixed It](./troubleshooting)  
  Real errors from writing my own scripts, broken down into problem, cause, fix and lesson.

---

## Learning Approach

- Concepts practised by writing and running real scripts, not just reading
- Scripts run both through VS Code and by hand in the terminal, to keep `chmod +x` and `./` familiar
- Edge cases tested on purpose: empty input, boundary values, missing arguments
- Mistakes written up instead of tidied away

---

## Folder Structure

```
02-bash/
├── README.md
├── fundamentals/
│   ├── README.md
│   ├── 01-script-basics.md
│   ├── 02-variables-and-quoting.md
│   ├── 03-parameters-and-input.md
│   ├── 04-arithmetic.md
│   ├── 05-conditionals.md
│   ├── 06-loops.md
│   ├── 07-functions.md
│   ├── 08-exit-codes-and-error-handling.md
│   └── 09-environment-and-path.md
└── troubleshooting/
    ├── README.md
    ├── 01-script-ran-old-code.md
    ├── 02-wrong-branch-no-error.md
    ├── 03-hidden-syntax-error.md
    ├── 04-bad-substitution.md
    └── 05-comment-in-the-wrong-place.md
```
