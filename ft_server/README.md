# 📚 ft_server
@42seoul : (2020.07.25 ~ 2020.08.08)

## About
- Docker를 활용하여 하나의 컨테이너에 Nginx, mysql, phpmyadmin, wordpress 서비스를 만드시오.
- 단, DockerHub를 사용하지 않고 직접 DOCKERFILE을 만듭니다. (OS : debian)

- 서비스 구성은 아래와 같습니다.


![ft_server_draw](https://user-images.githubusercontent.com/57086195/104842929-67727a00-590b-11eb-9cea-200bd22d97af.png)


- 조건
	- http://localhost -> https://localhost 리디렉션
	- localhost:80 -> https://localhost 리딕렉션
	- https://localhost/wordpress
	- https://localhost/phpmyadmin
	- wordpress, phpmyadmin은 mysql과 연결


## Run
1. `DOCKERFILE`, config file 생성
2. docker build -qt ft_server:kukim ./
3. docker run -it -p80:80 -p443:443 ft_server:kukim
4. 웹 서비스 시연


## Review
- 도커가 왜 필요한지 알게 되었고


### Reference


### Author
[kukim](https://github.com/ku-kim)
