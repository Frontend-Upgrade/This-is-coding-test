## 4-1. 상하좌우

### 아이디어
L, R, U, D 방향 이동에 대한 상수를 생성해 이동을 구현한다.

```js
const path = process.platform === "linux" ? "/dev/stdin" : "input.txt";
const input = require("fs")
  .readFileSync(path)
  .toString()
  .trim()
  .split("\n")
  .map(i => i.split(' '));

function solution(input) {
  let answer = [1, 1];
  const N = input[0][0];
  const plans = input[1];
  // L R U D
  const dir = [[0, -1], [0, 1], [-1, 0], [1, 0]];

  const move = (cur, d) => {
    let nx = cur[0] + d[0];
    let ny = cur[1] + d[1];

    if (nx < 1) nx = 1;
    if (nx > N) nx = N;
    if (ny < 1) ny = 1;
    if (ny > N) ny = N;

    return [nx, ny]
  }

  plans.forEach(plan => {
    if (plan === "L") {
      answer = move(answer, dir[0])
    }
    else if (plan === "R") {
      answer = move(answer, dir[1])
    }
    else if (plan === "U") {
      answer = move(answer, dir[2])
    }
    else {
      answer = move(answer, dir[3])
    }
  })

  console.log(answer)
}

solution(input)
```