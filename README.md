## C-NetworkProgramming
# c# Networkprogramming .. udp, tcp 하면서 알게되는 지식


1. **Task.WhenAll()**

[비동기 작업은 태스크 객체를 사용해 구성하라]
>태스크는 다른 리소스(주로 스레드)에 작업을 위임할 수 있도록 추상화한 개념이다.
>Task 타입은 객체이므로 메서드와 프로퍼티를 사용해서 조작할 수 있고, 여러 태스크를 모아서 거대한 태스크로 묶을 수도 있다.
>그리고 이렇게 묶인 태스크를 병렬 또는 순서대로 실행할 수도 있다.

```
public async Task<IEnumerable<string>> ReadStockNameAsync(IEnumerable<string> symbols)
{
    var resultTasks = new List<Task<string>>();

    foreach (var symbol in symbols)
    {
        resultTasks.Add(ReadSymbolAsync(symbol));
    }

    // 모든 Task 동시 수행
    var results = await Task.WhenAll(resultTasks);
    return results;
}
```

출처:https://hyeo-noo.tistory.com/426
