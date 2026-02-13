# 📄 get_next_line

*This project has been created as part of the 42 curriculum by pjelinek*

---

## 🧠 Description

The objective of this project is to implement a function capable of reading a file descriptor line by line.

`get_next_line` returns one line at a time from a given file descriptor, including the newline character if present.
Each call resumes reading where the previous one stopped, until the end of the file is reached.

The project focuses on low-level file I/O, memory management, and persistent buffering between function calls.

Core learning goals of the project:

* Understanding file descriptors and reading from them
* Managing dynamic memory allocation
* Handling buffers and partial reads
* Preserving state between function calls
* Dealing with edge cases (EOF, empty files, multiple FDs)

The implementation emphasizes reliability, efficiency, and correct memory handling.

---

## ⚙️ Compilation

Compile the project using:

```bash
make
```

Clean object files:

```bash
make clean
```

Remove all build artifacts:

```bash
make fclean
```

Rebuild from scratch:

```bash
make re
```

---

## 🔌 Usage

Include the header in your project:

```c
#include "get_next_line.h"
```

Compile with the source files or library:

```bash
cc main.c get_next_line.a
```

Example usage:

```c
int     fd;
char    *line;

fd = open("file.txt", O_RDONLY);
while ((line = get_next_line(fd)) != NULL)
{
    printf("%s", line);
    free(line);
}
close(fd);
```

---

## 🧩 Function Prototype

```c
char    *get_next_line(int fd);
```

Behavior:

* Reads from the given file descriptor
* Returns the next line including the newline character
* Returns `NULL` when the end of the file is reached or an error occurs

---

## 📁 Project Structure

```
get_next_line/
│
├── get_next_line.c        # main function logic
├── get_next_line_utils.c  # helper functions (string handling, memory, etc.)
├── get_next_line.h        # header file & prototypes
└── Makefile               # build rules
```

---

## 🔍 Implementation Notes

* Uses a static buffer to store remaining data between function calls.
* Reads from the file descriptor in chunks defined by `BUFFER_SIZE`.
* Extracts one line at a time from the buffer.
* Handles multiple file descriptors independently.
* Ensures no memory leaks by freeing used buffers appropriately.

The return behavior matches the subject requirements:

* valid line → returned string
* EOF or error → `NULL`

---

## 📎 Resources

* `man read`
* `man open`
* 42 get_next_line subject (official project PDF on the intra)
* C documentation on file descriptors and memory allocation

---

## 🤖 Note

AI was used for the exploratory part of this project
(conceptual understanding, buffering strategies, memory handling, and edge-case analysis).

