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

example

```cs
public static async Task<Datas> Load(string url, CancellationToken cancellationToken)
{
    using (UnityWebRequest request = UnityWebRequest.Get(url))
    {
        // 체크 포인트: 작업이 아직 진행 중인지 확인
        if (cancellationToken.IsCancellationRequested)
        {
            // 작업이 취소되었으므로 여기에서 종료하거나 예외를 throw할 수 있습니다.
            // 여기서는 Task를 취소하고자 AggregateException을 throw합니다.
            throw new TaskCanceledException();
        }

        await request.SendWebRequest();

        // 체크 포인트: 작업이 아직 진행 중인지 확인
        if (cancellationToken.IsCancellationRequested)
        {
            throw new TaskCanceledException();
        }

        if (request.result == UnityWebRequest.Result.Success)
        {
            result = request.downloadHandler.text;
            json = JsonParsing(result);
            //string tilesetText = JsonUtility.ToJson(json);
        }
        else
        {
            Debug.LogError("Can’t find data");
        }
    }

    return json;
}




CancellationTokenSource cancellationTokenSource = new CancellationTokenSource();
CancellationToken cancellationToken = cancellationTokenSource.Token;

// Load 메서드 호출 시 CancellationToken 전달
try
{
    Datas data = await YourClassName.Load("your_url", cancellationToken);
    // 다운로드 성공 처리
}
catch (TaskCanceledException)
{
    // 취소되었을 때의 처리
}

// 예를 들어, 버튼 클릭 시 작업 취소
yourCancelButton.onClick.AddListener(() => cancellationTokenSource.Cancel());
```
