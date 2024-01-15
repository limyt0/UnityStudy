01/15

﻿CancellationTokenSource tokenSource = new CancellationTokenSource();

await Task.aaaa(1000, tokenSource.Token);

aaaa의 param으로 token을 받으면 됨!
aaaa 안에서 
```cs
if (token.IsCancellationRequested)
{
    return; // 중단
}

if (token.IsCancellationRequested)
{
    yeild return break; // 중단
}

```
token.IsCancellationRequested를 통해 이런 식으로 중단 시켜줘야함!


// 토큰을 가진 모든 비동기 함수 종료.
tokenSource.Cancel();

주의: 한번 Cancel하고 재실행 그냥 하면 안 되니깐
tokenSource = new CancellationTokenSource()로 재선언 해줘야 함.

