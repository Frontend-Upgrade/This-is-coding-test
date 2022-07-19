## 4-2. 시각

### 아이디어

0시 ~ N시 59분 59초
시, 분, 초에 대해 3중 for문을 활용해 완전 탐색

```js
const path = process.platform === "linux" ? "/dev/stdin" : "input.txt";
const input = require("fs")
  .readFileSync(path)
  .toString()
  .trim()
  .split("\n")
  .map(i => i.split(' '));

function solution(input) {
  const N = Number(input[0][0])
  let answer = 0;

  for(let i = 0; i < N + 1; i++) {
    for (let j = 0; j < 60; j++) {
      for (let k = 0; k < 60; k++) {
        const clock = `${i}${j}${k}`
        if (clock.includes('3')) answer++;
      }
    }
  }

  console.log(answer)
}

solution(input)
```