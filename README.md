
# get_next_line 42

get_next_line is a project at 42 School that requires you to implement a function capable of reading a line from a file descriptor. The function must return a single line at a time, including the newline character if present.

## Requirements
 * A Unix-based operating system (Linux/MacOS)
 * C programming language
 * File descriptor handling

## Setup
Clone the repository :
```
  git clone https://github.com/BouhcineAmezouar7/get_next_line.git
  cd get_next_line
```

Compile the project:
```
  gcc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line.c get_next_line_utils.c -o gnl_test
```
This will generate an executable named gnl_test.

## Usage
Using get_next_line

Include get_next_line.h in your project and call get_next_line() with a file descriptor:
```
#include "get_next_line.h"
#include <fcntl.h>
#include <stdio.h>

int main()
{
    int fd = open("test.txt", O_RDONLY);
    char *line;
    while ((line = get_next_line(fd)))
    {
        printf("%s", line);
        free(line);
    }
    close(fd);
    return 0;
}
```

## Function Prototype

```
char *get_next_line(int fd);
```
* Reads a line from the file descriptor fd.

* Returns the line including the newline character (\n), if present.

* Returns NULL when there is nothing more to read or an error occurs.

## Features

* Reads one line at a time.

* Handles multiple file descriptors simultaneously.

* Uses a static buffer to store read data efficiently.


## Testing
To test get_next_line, compile and run with a test file:

```
  gcc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line.c get_next_line_utils.c main.c -o gnl_test
./gnl_test
```
