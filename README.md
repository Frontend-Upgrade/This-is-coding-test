## 이것이 취업을 위한 코딩테스트다

### 진행 방법

- Part 02에서 CHAPTER 03 (그리디) ~ CHAPTER 10 (그래프 이론)정리.
- 일주일에 한 챕터씩 진행하여 8월말에 끝내는 것을 목표로 합니다.
- 각 챕터마다 폴더를 만들어서 정리해주시기 바랍니다.

### 문제 풀이 방법
1. solve.js 파일, input.txt 파일 생성
2. 파일 작성
```js
// solve.js
const path = process.platform === "linux" ? "/dev/stdin" : "input.txt";
const input = require("fs")
  .readFileSync(path)
  .toString()
  .trim()
  .split("\n")
  .map(i => i.split(' '));

function solution(input) {

}

solution(input)

// input.txt
// 원하는 input
```
3. 파일 실행
```bash
node solve.js
```