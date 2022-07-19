## 4-3. 왕실의 나이트

### 아이디어

나이트가 움직일 수 있는 8방향에 대해 모두 탐색하고 움직일 수 있는 경우의 수를 센다.

```js
const path = process.platform === "linux" ? "/dev/stdin" : "input.txt";
const input = require("fs")
  .readFileSync(path)
  .toString()
  .trim()
  .split("\n")
  .map(i => i.split(' '));

function solution(input) {
  let answer = 0;

  const xArr = ["a", "b", "c", "d", "e", "f", "g", "h"];
  const x = xArr.indexOf(input[0][0][0]);
  const y = Number(input[0][0][1]) - 1;
  const dx = [-1, -1, -2, 2, 1, 1, -2, 2];
  const dy = [-2, 2, -1, -1, -2, 2, 1, 1];

  for (let d = 0; d < 8; d++) {
    const nx = x + dx[d];
    const ny = y + dy[d];

    if (nx > -1 && nx < 8 && ny > -1 && ny < 8) answer++;
  }

  console.log(answer);
}

solution(input)
```