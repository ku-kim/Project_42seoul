# 📠 Get_next_line
@42seoul : (2020.07.01 ~ 2020.07.15)

## 📖 About
- 이 프로젝트는 fd에 저장된 파일 내용을 "\n" 개행 단위 줄로 반환하는 함수를 구현합니다.(The aim of this project is to make you code a function that returns a line
ending with a newline, read from a file descriptor.)

|  Type   | Function | Description |   
| :---: | :--------: | :-----------: |
| `file read` | get_next_line(int fd, char **line) | Write a function which returns a line read from a file descriptor, without the newline.  |

## 📝 Review
- fd 관리와 static variable을 활용하는 방법을 배울 수 있었습니다.
- python의 read.csv() 함수를 만든다고 했을 때 단순히 "\n" 개행 단위로 행을 나누고 sep(구분자) 단위로 열을 나눌 수 있는데 C에서도 이제 Libft 프로젝트와 Get_next_line 프로젝트 함수를 합치면 쉽게 read.csv() 같은 함수를 만들 수 있다.

## 🏁 Run
- Read File
	1. Iris.csv(붓꽃 데이터)를 "\n"개행 단위로 읽기 -> get_next_line()
	2. 개행 단위로 읽은 데이터 user_output 으로 저장
	3. diff user_output ./Iris.csv

![get_next_line_fileread](https://user-images.githubusercontent.com/57086195/104798401-e41d2f80-5809-11eb-94e1-441b03ccfdd7.gif)


---

## 🔗 Reference
- [Test : GNL_lover](https://github.com/charMstr/GNL_lover)

## 🧑🏻‍💻 Author
[kukim](https://github.com/ku-kim)
