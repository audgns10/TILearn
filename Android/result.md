# Result?

<br>

```kt
sealed interface Result<out T> {
    data class Success<T>(val data: T): Result<T>
    data class Fail(val exception: Throwable): Result<Nothing>
    object Loading: Result<Nothing>
}

fun <T> Flow<T>.asResult(): Flow<Result<T>> = map<T, Result<T>> { Result.Success(it) }
    .onStart { emit(Result.Loading) }
    .catch { emit(Result.Fail(it)) }
```   

<br>

* 개발을 하면서 이러면 코드를 다른 깃허브 레포지토리에서 보게 되어서 공부를 하고 개발할때 사용해보려 한다.   
   
<br>

일단 이 코드에 대해서 설명을 하자면 ->

* Result는 제네릭 타입 T를 받는 seal interface 함수로 정의가 된다. -> 이 interface는 **성공, 실패, 로딩의 세가지의 상태**를 나타낸다.

* fun <T> Flow<T>.asResult(): Flow<Result<T>> 이러한 확장함수는 Flow<T>를 받아서 Flow<Result<T>> 변환을 한다. 이를 통해 비동기 작업의 결과를 Result 객체로 감싸고, 이를 Flow로 다룰 수 있습니다.

* { Result.Success(it) }: 각 flow의 요소를 받아서 **Success 상태의 Result를 객체로 매핑**을 한다
* onStart { emit(Result.Loading) }: flow가 **시작 상태**일때 **Loading이라는 상태의 Result를 먼저 방출**을 한다
* catch { emit(Result.Fail(it)) }: flow에서 발생이 되는 **예외**를 **catch해서 fail이라는 상태의 Result를 반환하고 방출**한다

* 결과적으로, asResult() 함수는 Flow의 각 요소를 **성공 상태의 Result로 매핑**하고, Flow가 **시작**될 때는 **Loading 상태의 Result를 방출**합니다. 만약 Flow에서 **예외가 발생**하면 이를 **에러 상태의 Result로 처리**합니다. 이렇게 함으로써 **비동기 작업의 성공, 실패, 진행 중인 상태를 간편하게** 다룰 수 있습니다.