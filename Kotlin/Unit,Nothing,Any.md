# Kotlin -> Unit, Nothing, Any


## Unit

```kt
class Foo {
    fun foo(): Unit {
        //
    }

    // 정수값을 반환하는 함수
    private fun bar(): Int{
        return 0
    }
}
```

<br>

```java
public class JavaFoo {
    private void foo() {
        //
    }

    private fun bar(): Int {
        return 0;
    }
}
```

* 코틀린에서 Unit은 하나의 타입인데 함수 자체를 의미한다 -> 자바의 void와 비슷함
* Unit 타입을 리턴하는 함수는 아래처음 선언할 때 선언하는 타입을 생략할 수 있다(아래 예시 있음)

```kt
class Foo {
    // 아무 값도 반환하지 않는 함수
    fun foo(){ // Unit를 붙이지 않아도 사용할 수 있다
        //
    }

    private fun bar(): Int {
        return 0
    }
}
```

<br>

```kt
class Foo {
    // 아무 값도 반환하지 않는 함수
    fun foo() { // Unit을 사용하지 않아도 사용할 수 있다
        println("foo() 호출")
    }

    // 정수값을 반환하는 함수
    fun bar(): Int {
        return 0
    }
}

fun main() {
    Foo().foo()

//  val a: Int = Foo().bar()
    val a = Foo().bar()
    println("a : ${a}")
}

/*
출력 ->

foo() 호출
a : 0
*/
```

* main()에서 foo()를 호출할 경우 foo() 안에 써둔 println()이 호출되고, bar()을 호출할 경우 Int 형태의 리턴값을 갖기 때문에 변수를 하나 선언해줘야 한다

<br>

## Any

* 코틀린에 존재하는 모든 타입은 Any를 상속한다

```kt
fun main() {
    val hi: Any = "안녕"
    val one: Any = 1
    val decimal: Any = 0.5
    
    println("hi = ${hi}")
    println("hi = ${one}")
    println("hi = ${decimal}")
}

/*
hi : 안녕
one : 1
decimal : 0.5
*/
```

* "안녕"이란 문자열은 본래 String 이지만 코틀린의 모든 타입은 Any를 상속하기 때문에 서브 클래스와 객체는 부모 클래스에 대입이 가능하다는 특징을 적용받는다. 그래서 String도 Any 타입에 대입이 가능하다

<br>

## Nothing

* 어떤 값도 포함하지 않는 타입이라는 걸 뜻하며, 코드 실행 흐름이 도착할 수 없는 영역을 나타내기 위한 특수 타입으로 사용된다 -> 예외를 던질 함수 유형을 정의하는 데 사용