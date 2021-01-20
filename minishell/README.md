# ⌨️ minishell
`heeheeshell` by [yeha](https://github.com/tomhato) and [kukim](https://github.com/ku-kim)  
@42seoul : (2020.11.10 ~ 2021.01.03)

## About
- 간단한 **쉘** 프로그램을 구현합니다.(The objective of this project is for you to create a simple shell.)
- 작동은 bash와 동일합니다.
- bash의 작동 방식, Standard Stream, foreground & background process, fork, IPC, pipe, execve, signal 등을 공부합니다.
- 이전 프로젝트 libft, get_next_line 활용
- 구현 목록
	- echo, exit, return value, env, export, unset, cd, pwd
	- $PATH
	- multiline string
	- 그 외 command : /bin/[command]
	- redir(<, >, >>)
	- pipe(|)

## Review
- 사전 지식을 얻기 위해 [OS 스터디](https://github.com/Kraken-Addicts/Operating-System)를 두 달 동안 진행하며 연습 문제도 함께 제출했다.
- 가장 많이 사용하는 **쉘**의 내부 동작을 알게 되었다. 개인적으로 매우 놀라운 일이다.ex)zsh에서 ls -al 명령어 실행하면 zsh는 자식 프로세스를 만들고 그 자식 프로세스는 /bin/ls 를 실행한다니! 놀랍지 아니한가?
- 부모/자식 프로세스 생성, IPC통신에 대해 이해하게 되었고 signal과 exit 종료 코드도 알게되었다.
- Nginx 서비스를 백그라운드로 실행할 때 어떻게 동작할까? 궁금했는데 이 프로젝트를 통해 부모/자식 프로세스 분기 후 부모 프로세스가 waitpid() 하지 않고 종료하면 된다는 것도 알게 되었다.
- 한 줄 평 : 아니 내가 쉘을 만들었다고? 👏👏👏👏

## Run
- echo, Multi line, exit, return value, ';' cat, cd, pwd
![heeheeshell_1](https://user-images.githubusercontent.com/57086195/104806644-60b90980-581c-11eb-8fbe-2c2e6c93fb28.gif)

- env, export, unset, Signal(Ctrl + C, \, D), redir, pipe 
![heeheeshell_2](https://user-images.githubusercontent.com/57086195/104806649-66aeea80-581c-11eb-984e-d0daff6a9c85.gif)

---

## Reference
- [man : bash](https://linux.die.net/man/1/bash)
- [gnu Bash Reference Manual](https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html)

## Author
[yeha](https://github.com/tomhato)  
[kukim](https://github.com/ku-kim)
