# 🖨 ft_printf
## About
- 이 프로젝트는 단순합니다. <stdio.h>의 `printf()` 함수를 직접 구현합니다.(This project is pretty straight forward. You will recode printf)

## Run
- Simple Unit Test : Hello World! & %(c, s, p d, i, u, x, X, %)
![ft_printf_simple](https://user-images.githubusercontent.com/57086195/104793652-0487c280-57e7-11eb-93c0-3e68a0daa440.gif)

- All Test : reference 코드를 참고로 테스트 하였습니다.
![ft_printf_pft](https://user-images.githubusercontent.com/57086195/104793648-02256880-57e7-11eb-81e0-e9ce46372826.gif)


## Review
- C에서 가장 먼저, 많이(?) 쓰는 함수 `printf("Hello World!");` 를 사용하지 않고 내가 직접 구현한다니!! 신선한 충격이었다 🎃
- printf()가 <unistd.h>의 `write()` 기반으로 구현되어 있으며 문자열 파싱과 가변인자 처리를 어떻게 하는지 배울 수 있었다. width, precision 계산은 덤이었다.
- 흔히 자주 사용하는 함수들의 원형을 직접 구현할 수 있는 경험을 갖게 되었고 이 경험을 통해 특정 함수를 단순히 사용하는 것이 아닌 호기심이 생겼고, 나도 구현할 수 있다는 용기를 갖게 되었다.

## Function List
- `conversion`: c, s, p, d, i u, x, X, %
- `flag`: -, 0, ., *

### Reference
- [Test : PFT_2019](https://github.com/cclaude42/PFT_2019)

### Author
[kukim](https://github.com/ku-kim)
