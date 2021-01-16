# 📚 libft
@42seoul : (2020.04.15 ~ 2020.05.01)
## About
- 일반적으로 C언에서 자주 사용하는 함수들을 **직접** 구현합니다. (The aim of this project is to code a C library regrouping usual functions that you’ll be allowed to use in all your other projects.)

## Run
- [Unit Test](https://github.com/alelievr/libft-unit-test) : All Success
- Benchmark (My functions vs Libc)
	- 완패..

[![asciicast](https://asciinema.org/a/384736.svg)](https://asciinema.org/a/384736)


- test script
<script id="asciicast-384699" src="https://asciinema.org/a/384699.js" async></script>

## Review
- C에서 include하여 사용하는 `<ctype.h>`, `<string.h>` `<stdlib.h>`의 함수 뿐만 아니라 자주 사용되는 split, join 함수 등 직접 구현하면서 C의 기본 문법과 포인터 연산, 메모리 관리(Heap), Makefile 등 배울 수 있었다.
- Libc에 이미 구현되어 있는 함수들을 가져다 쓰면 되는데 과제하면서 왜 내가 구현해야할까 고민도 많이 했지만 직접 밑단에서 함수가 이렇게 동작하는구나 생각할 수 있어서 무척 유익했다. GNU의 Libc와 내가 짠 코드 벤치마킹 했는데 처참하게 무너졌다. Libc는 어셈블리로 완벽히 최적화 되어있어 당연한 결과였지만 눈으로 보니 비참하면서 약간 욕심이 생겼다. 하지만 욕심만 갖고 다른 프로젝트를 하자.

## Function List
- [Libc Functions](#📕-Libc-functions-(Standard-C-Library)) : `<ctype.h>`, `<string.h>` `<stdlib.h>`
- [Non- Libc Functions](#📗-Additional-functions)
- [Linked-list Functions](#📘-Linked-list)


---

# Function List
## 📕 Libc functions (Standard C Library)
- `<ctype.h>`, `<string.h>` `<stdlib.h>`의 몇 가지 함수를 구현합니다.

Description : man [function]

| Type | Function |
|:---:|:--------:|
|`<string.h>` : memory | `memset`, `memcpy`, `memccpy`,`memmove`, `memchr`, `memcmp` | 
|`<string.h>` : string | `strlen`, `strlcpy`, `strlcat`, `strchr`, `strrchr`, `strnstr`, `strncmp`, `strdup` | 
|`<stdlib.h>`| `calloc`, `atoi` | 
|`<ctype.h>`| `isalpha`, `isdigit`, `isalnum`, `isascii`, `isprint`, `toupper`, `tolower`| 

## 📗 Additional functions
- libc에 포함되지 않지만 자주 사용하는 함수를 구현합니다.
- string : 문자열 처리 함수
- put_fd : 문자열 출력 함수

|  Type   | Function | Description |
| :---: | :--------: | :----------- |
| `string` | ft_substr | Allocates (with malloc(3)) and returns a substring from the string ’s’. The substring begins at index ’start’ and is of maximum size ’len’. |
| `string` | ft_strjoin | Allocates (with malloc(3)) and returns a new string, which is the result of the concatenation of ’s1’ and ’s2’. |
| `string` | ft_strtrim | Allocates (with malloc(3)) and returns a copy of ’s1’ with the characters specified in ’set’ removed from the beginning and the end of the string. |
| `string` | ft_split | Allocates (with malloc(3)) and returns an array of strings obtained by splitting ’s’ using the character ’c’ as a delimiter. The array must be ended by a NULL pointer. |
| `string` | ft_itoa | Allocates (with malloc(3)) and returns a string representing the integer received as an argument. Negative numbers must be handled. | 
| `string` | ft_strmapi | Applies the function ’f’ to each character of the string ’s’ to create a new string (with malloc(3)) resulting from successive applications of ’f’. |
| `put_fd` | ft_putchar_fd | Outputs the character ’c’ to the given file descriptor. |
| `put_fd` | ft_putstr_fd | Outputs the string ’s’ to the given file descriptor. |
| `put_fd` | ft_putendl_fd | Outputs the string ’s’ to the given file descriptor, followed by a newline. |
| `put_fd` | ft_putnbr_fd | Outputs the integer ’n’ to the given file descriptor. |

## 📘 Linked list
- 링크드 리스트를 구현합니다.

|  Type  | Function | Description |
| :---: | :-------: | :---------- |
| `linked-list` | ft_lstnew | Allocates (with malloc(3)) and returns a new element. The variable ’content’ is initialized with the value of the parameter ’content’. The variable ’next’ is initialized to NULL.|
| `linked-list` | ft_lstadd_front | Adds the element ’new’ at the beginning of the list. |
| `linked-list` | ft_lstsize | Counts the number of elements in a list. |
| `linked-list` | ft_lstlast | Returns the last element of the list. |
| `linked-list` | ft_lstadd_back | Adds the element ’new’ at the end of the list. |
| `linked-list` | ft_lstdelone | Takes as a parameter an element and frees the memory of the element’s content using the function ’del’ given as a parameter and free the element. The memory of ’next’ must not be freed. |
| `linked-list` | ft_lstclear | Deletes and frees the given element and every successor of that element, using the function ’del’ and free(3). Finally, the pointer to the list must be set to NULL. |
| `linked-list` | ft_lstiter | Iterates the list ’lst’ and applies the function ’f’ to the content of each element. |
| `linked-list` | ft_lstmap | Iterates the list ’lst’ and applies the function ’f’ to the content of each element. Creates a new list resulting of the successive applications of the function ’f’. The ’del’ function is used to delete the content of an element if needed. |

---

## Reference
- [man : <string.h>](https://man7.org/linux/man-pages/man0/string.h.0p.html)
- [man : <stdlib.h>](https://man7.org/linux/man-pages/man0/stdlib.h.0p.html)
- [man : <ctype.h>](https://man7.org/linux/man-pages/man0/ctype.h.0p.html)
- [Linft Unit Test : Benchmark code](https://github.com/alelievr/libft-unit-test)


## Author
[kukim](https://github.com/ku-kim)
