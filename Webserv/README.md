# 🤖 Webserv
`Youpi Webserv` by [yeha](https://github.com/tomhato), [yeosong](https://github.com/yeosong1) and [kukim](https://github.com/ku-kim)  
@42seoul : (2021.02.10 ~ 2021.05.03)

## 📖 About
- `Nginx`와 유사한 웹서버 개발
- 멀티 프로세스, 쓰레드가 아닌 `멀티 플렉싱(Multiplexing)`을 활용하여 구현합니다.
- 작동은 Nginx와 유사하게 conf 파일로 웹서버를 셋업합니다.
- Keyword : Socket Programming, HTTP/1.1 Request & Response, HTTP/1.1 Methods RFC, TCP/IP, Network, Multiplexing, Non-Blocking, Asynchronous, CGI, Webserver(Nginx)

## 📝 Review
- 팀 프로젝트 진행을 위한 구글 코딩 컨벤션, github, Branch Workflow를 설정, 기능마다 코드리뷰, 페어코딩, 마지막에 refactoring 하기로 했다.
- 전반적으로 사전 지식이 없기 때문에 C를 활용한 소켓 프로그래밍을 중심으로 학습해가며 상황에 맞게 개선했다.
	- i.e. 싱글프로세스 웹서버의 한계 : 다수의 클라이언트 응답 처리 딜레이 문제
		- 멀티프로세스, 멀티스레드, 멀티플렉싱 선택지 중 멀티플렉싱 선택
	- i.e. 멀티 플렉싱 서버 구현 문제점 : 클라이언트의 요청에 따라 서버 자원을 read, write 하는데 fd에 Blocking이 걸려 지연 발생
		- fcntl()을 사용해 해당 fd를 Non-blocking 설정
	- i.e. 클라이언트가 비정상 종료했을 때
		-  서버 측에서 sigpipe의 시그널을 체크하고 비정상 종료 때 해당 socket fd 닫기
	- i.e. 서버 비정상 종료, 재시작 Time-wait bind() 재할당 문제
		- SO_REUSEADDR 옵션으로 bind() 문제 제거
	- i.e. RFC 문서에 따라 HTTP/1.1 헤더를 구현하는데 크고 작은 어려움들이 많았고 실제로 구현되어 있는 부분에 대한 이해가 깊어졌다.
		- e.g. `Accept-Language` 요청에 따라 content negotiation 하는 알고리즘이 RFC 문서에 특정하지 않기 때문에 직접 구현했다.
		- e.g. `Transfer-Encoding:chunked` 요청 헤더가 있다면 서버측에서 전송할 때 데이터를 나눠서 보내고 끝 메세지에 개행 두번 + EOF
		- e.g. nginx에서 리다이렉트와 리버스 프록시를 손쉽게 사용하는데 구현은 클라이언트 특정 리소스 요청이 redirect 되는 리소스라면 서버 측에서 단순하게 클라이언트에게 redirect 되었다고 `Location:uri` 응답 헤더를 보낸다. 이에 클라이언트가 해당 리소스에 재요청 한다. 리버스 프록시는 서버측에서 `Location:uri`를 클라이언트에게 보내지 않고 리다이렉트된 리소스를 찾아 클라이언트에게 응답해준다. 구현할 땐 아주 단순한 부분이지만 기능 차이가 크다.
- 개선 사항
	- 현재 서버는 멀티 플렉식 (select() + fcntl()(non-blocking  + asynchronous))으로 되어있지만 cgi를 제외하고 싱글 프로세스로 작동한다. nginx에서는 conf 파일에서 Worker Process 을 설정으로 프로세스 개수를 설정할 수 있는데, 현재 구현한 webserv에서도 cpu 작업이 오래걸리는 요청이 있다면 애초에 멀티 프로세스,스레드를 만들어 처리하면 처리 속도가 증가할 수 있겠다.
	- 테스트 코드와 refactoring에 빈약하다.
	- 웹서버의 log가 부족하다.

## 🏁 Run

- HTTP Method test : GET, HEAD, POST
![Methods2](https://user-images.githubusercontent.com/57086195/122648307-a54a2780-d163-11eb-9866-eb5be27841a7.gif)

- Content negotiation, Redirect
![nego_redir](https://user-images.githubusercontent.com/57086195/122648272-6c11b780-d163-11eb-875d-99bc4efd59c1.gif)

- Authorization, Server pause 503, Siege test
![auth_503_siege](https://user-images.githubusercontent.com/57086195/122648285-91062a80-d163-11eb-9e77-7976946e4cc2.gif)


---

## 구현 사항 
- nginx
	- config file
	- Host, Port
	- Server name
	- setup default
	- limit client body size
	- Accepted HTTP Methods for the route
	- autoindex On/Off
	- redirect
	- execute CGI (RFC 3275 참고)
- HTTP 헤더(RFC 7230 ~ 7235, HTTP/1.1을 참고하여 아래 헤더를 구현합니다.)
	- Accept-Charsets
	- Accept-Language
	- Allow
	- Authorization
	- Content-Language
	- Content-Length
	- Content-Location
	- Content-Type
	- Date
	- Host
	- Last-Modified
	- Location
	- Referer
	- Retry-After
	- Server
	- Transfer-Encoding
	- User-Agent
	- WWW-Authenticate
## 🔗 Reference
- [man : bash](https://linux.die.net/man/1/bash)
- [gnu Bash Reference Manual](https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html)

## 🧑🏻‍💻 Author
[yeha](https://github.com/tomhato)  
[kukim](https://github.com/ku-kim)
