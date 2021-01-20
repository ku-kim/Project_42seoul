# 📚 Philosophers
@42seoul : (2021.01.04 ~ )

## About
- 이 프로젝트는 기본적인 프로세스 스레딩, mutex, semaphore, shared memory을 배웁니다.(In this project, you will learn the basics of threading a process and how to work on the same memory space. You will learn how to make threads. You will discover the mutex, semaphore and shared memory.)
- C언어를 활용하여 [Dining philosophers problem](https://en.wikipedia.org/wiki/Dining_philosophers_problem) 문제를 3가지 방법으로 구현합니다.


![philo](https://upload.wikimedia.org/wikipedia/commons/7/7b/An_illustration_of_the_dining_philosophers_problem.png)

#### 프로그램 사항
1. Program 1 `philo_one` : Mutex
	- 철학자는 쓰레드이다.
	- 원탁에 앉아있고, 양 옆에 포크가 있다.
2. Program 2 `philo_two` : Semaphore
	- 철학자는 쓰레드이다.
	- 원탁에 앉아있고, 테이블 중앙에 포크가 있다.
3. Program 3 `philo_three` : shared memory
	- 철학자는 프로세스이다.
	- 원탁에 앉아있고, 테이블 중앙에 포크가 있다.

- 조건
	- 철학자는 2명 이상이다.
	- 철학자는 정해진 시간 안에 먹지 않으면 죽는다.
	- 철학자 한 명이 죽으면 프로그램을 종료한다. (죽는 시간 기준10ms 안에 종료 메세지를 보내야 한다.)
	- 철학자는 먹기위해 포크 2개를 집어야 한다.
	- 철학자는 먹고 -> 자고 -> 생각하는 것을 반복한다.
	- 프로그램 실행 인자는 총 5개 or 6개이다.
	- `./philo_one number_of_philosophers time_to_die time_to_eat time_to_sleep [number_of_times_each_philosopher_must_eat]`
	- ex) `./philo_one 2 310 100 100 2` 으로 실행한다면
		- 철학자 수 2명
		- 310ms안에 먹어야 철학자 생존
		- 100ms동안 먹는다
		- 100ms동안 잔다
		- 모든 철학자가 2번 먹으면 프로그램 종료 
	- 철학자는 프로그램에 따라 쓰레드이기도 하고 프로세스이기도 하다.

## Review
- 쓰레드나 프로세스 사이에 실행 시기를 맞추는 동안(동기화(Synchronization))에 문제가 발생할 수 있다.
- 예를 들어 A, B, C 쓰레드가 공유하고 있는 `int count`라는 변수를 동시에 수정한다면 결과가 이상하게 나올 것 이다. 또한 두 개의 작업이 서로 상대방의 작업이 끝나길 무한히 기다리거나(deadlock, 교착상태) 우선순위가 낮아서 아예 자원할당을 받지 못하는 경우도 있다(stravation, 기아상태).
- 이를 해결하기 위해 공유하고 있는 data를 Exclusive Access, 어느 한 스레드가 공유 변수를 사용하는 동안 다른 스레드가 접근하지 못하도록 막는 방법을 공부했다.
- Mutex와 Semaphore에 대한 이론적 개념과 이를 간단한 예제를 통해 구현할 수 있었다.

## Run
- Test
	- ./program 5 800 200 200 7 : 7번 다 먹으면 프로그램 종료
	- ./program 4 410 200 200 : 무한 루프
	- ./program 2 310 200 100 (10ms 안에 죽는 것 확인)

1. philo_one : Mutex version

![philo_one](https://user-images.githubusercontent.com/57086195/105130787-01643d80-5b2b-11eb-8ce9-a1f6b5b0f80d.gif)

2. philo_two : Semaphore version

![philo_two](https://user-images.githubusercontent.com/57086195/105130785-00cba700-5b2b-11eb-9fd7-7aedf9ee24b3.gif)


3. philo_three : Shared memory version

![philo_three](https://user-images.githubusercontent.com/57086195/105130782-ff01e380-5b2a-11eb-96a2-595089402d80.gif)

---

## Reference
- [wiki : Dining philosophers problem](https://en.wikipedia.org/wiki/Dining_philosophers_problem)
- [Dining Philosopher Problem Using Semaphores](https://www.geeksforgeeks.org/dining-philosopher-problem-using-semaphores/)
- [운영체제: 16. 철학자들은 왜 굶어 죽었을까? (철학자들의 저녁식사 문제)](https://youtu.be/YAP0Bv_aQl8)
- [06.6 기아상태](https://youtu.be/07d7I6GnCZ0)

## Author
[kukim](https://github.com/ku-kim)
