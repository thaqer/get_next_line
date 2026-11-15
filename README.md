# get_next_line

A 42 Amman project: `get_next_line(fd)` returns the next line read from a file descriptor, including its `\n`, or `NULL` at end of file or on error. Call it in a loop to read a file one line at a time. The caller frees each returned line.

The read size is set at compile time with `BUFFER_SIZE` (default `9`).

## Usage

```c
#include "get_next_line.h"
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
	int		fd = open("file.txt", O_RDONLY);
	char	*line;

	while ((line = get_next_line(fd)))
	{
		printf("%s", line);
		free(line);
	}
	return (0);
}
```

```sh
cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 main.c get_next_line.c get_next_line_utils.c
```

There is no Makefile; the project is meant to be compiled together with your own code.

## Author

[thaqer](https://github.com/thaqer), 42 Amman. Originally kept in [42amman_journey](https://github.com/thaqer/42amman_journey).
