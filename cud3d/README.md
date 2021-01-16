# 📚 cub3d
@42seoul : (2020.09.15 ~ 2020.11.02)
## About
- 이 프로젝트는 90년대 최초의 1인칭 슈팅 게임(`Wolfenstein 3D`)을 직접 만드는 것입니다.(This project is inspired by the world-famous eponymous 90’s game(`Wolfenstein 3D`), which was the first FPS ever)
- `ray casting` 알고리즘을 공부합니다.

- 구현
	- mapfile에 따라 그래픽이 다르게 출력
	- 벽, 장애물 통과 불가
	- --save 통해 플레이어 시작점 screenshot 저장
	- W,A,S,D,Q,E를 통해 이동, 시점 변환 가능, ESC 키 입력시 게임 종료
	- BGM, HUB 추가

## Review
- C로 컴퓨터 그래픽 알고리즘을 구현해 게임을 만든다는 상상도 못했다. 
- 2D 화면을 3D 처럼 보이게 만드는 `ray casting` 기술은 놀라웠다.(수학이 어려웠지만... 잘 구현했다.)
- 디테일하지 못한 부분도 많고, 완벽한 `Wolfenstein 3D`와 같진 않지만 추가 사항으로 HUB(Head up display)와 BGM 등 추가적인 요소를 넣으면서 게임 개발의 약간의 흥미를 갖게 되었다.
- BGM을 사용을 위해 부모/자식 프로세스 fork() 활용
- 추가 개선사항 : multi thread, 마우스 사용, 게임적인 요소, 자연스러운 움직임

## Run
- Basic Version

![cub3d_basic](https://user-images.githubusercontent.com/57086195/104799397-25194200-5812-11eb-9c68-26f848ef381f.gif)

- screenshot

![cub3d_screenshot](https://user-images.githubusercontent.com/57086195/104799400-29455f80-5812-11eb-8b69-e327000a386d.gif)

- 인터스텔라 Version

![cub3d_bonus](https://user-images.githubusercontent.com/57086195/104799399-277b9c00-5812-11eb-8e29-1a71948232d8.gif)


---

## Reference
- [Original Game Wolfenstein 3D](http://users.atw.hu/wolf3d/)
![wolf3d](https://user-images.githubusercontent.com/57086195/104798832-3ad83880-580d-11eb-8ddc-eca9e64e0297.png)


## Author
[kukim](https://github.com/ku-kim)
