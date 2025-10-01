# 1. 어려웠던 부분/문제

인상 깊었던 것들로 정리
1. [[2-2 삼각형의 완성 조건 (1) v]]
2. [[2-5 점의 위치 구하기 v]]
3. [[2-7 순서쌍의 개수 v]]
4. [[2-12 문자반복 출력하기 v]]
5. [[2-17 배열 두배 만들기 v]]
6. [[2-20 옷가게 할인 받기 v]]
# 2. 새롭게 알게 된 점

이번주는 배열 메소드를 많이 배웠다.
배열 메소드를 활용한 문제가 많았고 메소드를 알면 쉽게 풀렸다.

1. map() - 요소 편집
2. filter() - 조건에 맞는 요소 추리기
3. sort() - 정렬

### 배열에 요소가 속하는지(어디있는지)에 관한 메소드 들

4. arr.**indexOf**(searchElement[, fromIndex])  
5. arr.**lastIndexOf**(searchElement[, fromIndex])
6. arr.**includes**(valueToFind[, fromIndex])
7. arr.**findIndex**(callback(element[, index[, array]])[, thisArg])
8. arr.**some**(callback(element[, index[, array]])[, thisArg])

### 문자열 메소드 vs 배열 메소드

문자열도 배열과 메소드를 공유하는게 많았지만
기능이 조금 다르게 작동하는 것들도 있었다.

예를 들면 .includes
- 배열 => 요소의 존재여부를 반환
- 문자열 => 문자열 속에 특정 문자열이 속해 있는지 반환
이다.

비슷해보이지만 굳이 따지자면 문자열은 한 글자가 한 요소라고 생각해서
문자 배열을 찾을 수 있다는 점이 특이했다.

### 문자열 메소드

1) .replace('문자열', '바꿀 문자열') - 탐색 중 처음 발견한 한 문자열만 바꿈
2) .replaceAll('문자열', '바꿀 문자열') - 모든 일치하는 문자열 바꿈 
3) .repeat(n) - 특정 문자열을 n번 반복한 문자열 반환
4) .split(c) - 특정 문자열 기준으로 나눠서 배열 반환


### 정수 만들기
```JS
//정수 만들기
Math.floor(n)
parseInt(n)

//정수 판단
n%1===0
Number.isInteger(n)
```

# 3. 궁금한 점

아직 재귀 함수로 푸는 걸 못봤습니다.

# 4. 풀면서 느낀점

[프로그래머스 스쿨](https://school.programmers.co.kr/learn/courses/30/lessons/120809/solution_groups?language=javascript)

???
# 5. 문제 풀이 인증 (풀이 완료화면 스크린샷)

![[week2 풀이인증.png]]