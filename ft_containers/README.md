# 📚 ft_containers
@42seoul : (2021.02.02 ~ 2020.03.09)
## 📖 About
- 이 프로젝트는 C++ STL 라이브러리의 몇 가지 Container를 이해하기 위해 직접 구현해봅니다. (In this project you will implement the various container types of the C++ standard template library.)
- 구현 사항
	- C++ 98을 따릅니다.
	- :white_check_mark: List
	- :white_check_mark: Vector
	- :white_check_mark: Map
	- :white_check_mark: Stack
	- :white_check_mark: Queue
	- :white_check_mark: 각각의 컨테이너에 맞는 iterator

## 📝 Review
- STL의 컨테이너들을 직접 구현하면서 가장 큰 이점은 단순히 STL 함수 사용법을 아는 것을 넘어 [microsoft/STL](https://github.com/microsoft/STL) 오픈소스를 따라갈 수 있었으며 실제 구현이 어떻게 되어있는지 확인할 수 있었다. 이는 앞으로 어떤 함수든 구현사항을 뜯어볼 수 있다는 생각에 두려움이 사라졌다.
- 각 컨테이너를 구현하기 위해 자료구조를 이론적으로만 아는 것이 아닌 실제로 구현하니 좀 더 와닿았다.
	- i.e. vector는 동적 배열로 배열 크기의 재할당을 사용자가 신경쓰지 않고 사용하는 매우 유용한 컨테이너, 자료구조이다. (Python의 List도 동적 배열이다) 기존 C, CPP에서 동적배열 자료구조를 사용하지 않고 할당한 배열 크기를 넘었을 때는 재할당 해야하는 번거로움을 벗어난다는 구현하는데 있어 동적 할당 된 배열의 크기를 증가할 때 마다 새롭게 동적 할당하여 추가하는 문제를 해결했다. 이때 재할당 크기를 얼마만큼 사이즈를 설정해야할까를 찾던 중 `Growth Factor`의 값을 설정하여 (STL 기준 2) 동적할당 한다는 구현 방식이 새로웠다.
	- i.e. Map 컨테이너를 구현할 때 STL은 Red-Black tree로 구현되어 있다. 실제로 나만의 Map을 구현할 때 처음에는 단순 Binary tree로 구현하였는 데 트리 불균형 문제로 검색하는 데 O(log n)을 지키지 못했다. 이를 해결하기 위해 AVL-Tree 자료구조로 구현하였고 Red-Black tree와 같은 평균과 최악의 경우 검색,삽입,삭제 모두 O(log n)으로 구현할 수 있었다.
	- 컨테이너들의 시간, 공간 복잡도 개선해야 한다. 같은 기능이어도 .size()를 찍어보면 큰 차이가 발생했다.

---

## 🔗 Reference
- [microsoft/stl](https://github.com/microsoft/STL)
- [cplusplus-Containers](http://cplusplus.com/reference/stl/)
- [STL Headers](https://cs.stmarys.ca/~porter/csc/ref/stl/headers.html)
- [An introduction to C++ Traits](https://accu.org/journals/overload/9/43/frogley_442/)
- [avl-trees](https://www.codesdope.com/course/data-structures-avl-trees/)
- [코드없는 프로그래밍](https://www.youtube.com/channel/UCHcG02L6TSS-StkSbqVy6Fg/playlists?view=50&sort=dd&shelf_id=2)

## 🧑🏻‍💻 Author
[kukim](https://github.com/ku-kim)
