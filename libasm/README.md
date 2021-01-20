# 0️⃣1️⃣ libasm
@42seoul : (2020.11.20 ~ 2020.12.01)

## About
- 이 프로젝트는 어셈블리 언어를 가지고 몇 가지 함수를 구현합니다.(The aim of this project is to get familiar with assembly language.)

|  Type   | Function | Description |
| :---: | :--------: | :----------- |
|<string.h> | ft_strlen.s | man strlen |
|<string.h> | ft_strdup.s | man strdup |
|<string.h> | ft_strcpy.s | man strcpy |
|<string.h> | ft_strcmp.s | man strcmp |
|<fcntl.h> | ft_write.s | man write |
|<fcntl.h> | ft_open.s | man open |

- write, read 함수는 systemcall 호출하고 error 발생 시 __error 호출하여 errno를 저장하고 끝내야 합니다.

## Review
- assembly language를 경험할 수 있었다.
- [Computer-Achitecture 스터디](https://github.com/Kraken-Addicts/Computer-Achitecture)도 함께 진행했다.
- CPU, 레지스터, Stack 메모리를 이해하게 되었고 read, write함수를 구현하면서 각각의 시스템콜 번호를 호출하면 커널모드로 변경 되며 sys_open() 커널 함수가 호출되고 함수가 끝나면 다시 사용자 모드로 바뀌고 결과가 리턴된다. 이때 시스템콜이 에러가 발생하면 캐리플래그가 발생되고 rax 레지스터에 errno가 들어있다. 이것을 __error를 호출하여 error를 나타내는 변수에 rax 결과를 저장한 뒤 최종적으로 -1을 리턴하고 종료된다.
- Level 0 프로젝트 [Libft](https://github.com/ku-kim/Project_42seoul/tree/master/libft)에서 만들었던 ft_strlen과 Libc의 strlen 벤치마크 결과 완패했는데 그 이유가 어셈블리 단에서 최적화 과정을 거쳤기 때문이지 않을까 한다.

## Run
- Assembly Env
	- nasm compiler
	- x86_64 macos
	- intel
- Unit-test : Libc - 어셈블리 구현 함수 비교
![libasm](https://user-images.githubusercontent.com/57086195/104812738-9de6c100-5847-11eb-8be1-e458c7862e9d.gif)

├── Makefile  
├── ft_read.s  
├── ft_strcmp.s  
├── ft_strcpy.s  
├── ft_strdup.s  
├── ft_strlen.s  
├── ft_write.s  
├── libasm.h  
└── main.c  


---

## Reference
- [nasm](https://www.nasm.us/)

## Author
[kukim](https://github.com/ku-kim)
