## 4-4. 게임 개발

### 아이디어

규칙에 따 완전 탐색

```js
const path = process.platform === "linux" ? "/dev/stdin" : "input.txt";
const input = require("fs")
  .readFileSync(path)
  .toString()
  .trim()
  .split("\n")
  .map((i) => i.split(" "));

function solution(input) {
  let answer = 0;
  const [N, M] = input[0].map((i) => Number(i));
  let [x, y, d] = input[1].map((i) => Number(i));
  const map = [];

  for (let i = 0; i < N; i++) {
    map.push(
      input[i + 2].map((i) => {
        if (i === "1") return 2;
        else return Number(i);
      })
    );
  }

  map[x][y] = 1;

  const dx = [-1, 0, 1, 0];
  const dy = [0, 1, 0, -1];

  const turnLeft = () => {
    return d > 0 ? d - 1 : 3;
  };

  let tmpCount = 0;
  while (true) {
    if (map[x][y] === 0) {
      map[x][y] = 1;
      answer++;
    }

    d = turnLeft(d);
    let nx = x + dx[d];
    let ny = y + dy[d];

    if (nx > -1 && nx < N && ny > -1 && ny < M && map[nx][ny] === 0) {
      map[nx][ny] = 1;
      x = nx;
      y = ny;
      tmpCount++;
      answer++;
      continue;
    } else {
      tmpCount++;
    }

    if (tmpCount === 4) {
      nx = x - dx[d];
      ny = y - dy[d];
      // 바다가 아니면
      if (nx > -1 && nx < N && ny > -1 && ny < M && map[nx][ny] !== 2) {
        x = nx;
        y = ny;
      } else break;
      tmpCount = 0;
    }
  }

  console.log(map, answer);
}

solution(input);
```
