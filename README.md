# get_next_line

## 📖 Description

**get_next_line** is a project from the 42 School curriculum. The goal is to create a function that reads a file or input stream line by line, returning one line ending with a `\n` at each function call.

The function must handle different file sizes and buffer sizes while managing memory efficiently. It also needs to work with multiple file descriptors without losing track of their individual reading positions.

## 🛠️ Features

- Reads a file one line at a time.
- Handles different `BUFFER_SIZE` values.
- Works with standard input (`stdin`).
- Handles newline characters (`\n`).
- Supports files that do not end with a newline.
- Properly manages memory and avoids memory leaks.
- Supports multiple file descriptors (bonus).

## ⚙️ Compilation

Compile the mandatory part:

```bash
cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 \
get_next_line.c get_next_line_utils.c main.c
```

Compile the bonus part:

```bash
cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 \
get_next_line_bonus.c get_next_line_utils_bonus.c main.c
```

You can change `BUFFER_SIZE` to test different buffer sizes.

## 🚀 Usage

Example:

```c
#include "get_next_line.h"
#include <fcntl.h>
#include <stdio.h>

int main(void)
{
    int     fd;
    char    *line;

    fd = open("test.txt", O_RDONLY);
    if (fd == -1)
        return (1);

    while ((line = get_next_line(fd)) != NULL)
    {
        printf("%s", line);
        free(line);
    }

    close(fd);
    return (0);
}
```

## 📋 Function Prototype

```c
char *get_next_line(int fd);
```

**Return values:**
- A line read from the file descriptor, including `\n` if present.
- `NULL` when there is nothing left to read or when an error occurs.

## ⭐ Bonus

The bonus part extends the mandatory implementation by allowing multiple file descriptors to be read independently.

This means you can alternate between different files without losing the reading position of each one.

**Bonus features:**
- Manage multiple file descriptors simultaneously.
- Maintain a separate static buffer for each file descriptor.
- Read from different files in any order.
- Preserve the remaining content of each file between function calls.

## 🧠 What I Learned

Through this project, I improved my understanding of:

- File descriptors and the `read()` system call.
- Static variables.
- Dynamic memory allocation.
- String manipulation in C.
- Buffer management.
- Memory management and leak prevention.
- Handling multiple file descriptors.

## 👤 Author

gvasylie

