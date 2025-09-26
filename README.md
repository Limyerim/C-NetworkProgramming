## C-NetworkProgramming
# c# Networkprogramming .. udp, tcp 하면서 알게되는 것들


# 1. Task.WhenAll()

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

# 2. WireShark 프로그램 
   > 통신할 때 네트워크 패킷을 감시 및 분석하는 프로그램

조건문 이용해서 내가 원하는 주소로 들어오는 패킷 감시, 분석 가능

# 3. GUI - Dispatcher
> 오류: 다른 스레드가 이 개체를 소유하고 있어 호출한 스레드가 해당 개체에 액세스할 수 없습니다. 
> GUI 스레드에서 할당된 변수를 다른 스레드에서 바꾸려 할 때 에러 발생( Cross Thread 문제)
> 이 떄, *Dispatcher.Invoke** 나 **Dispatcher.BeginInvoke** 사용

- Invoke: 동기
- BeginInvoke: 비동기
