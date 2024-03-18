# android -> invoke

* 내가 위의 개념을 공부를 하게 된 개념은 여러가지 선배님들의 repo를 보다가 clean architecture + mvvm 의 방식을 따른 것들인데 여기서 domain 모듈에 있는 usecase에서 invoke를 사용해서 코드를 짜는 것을 보았다. 그래서 나는 invoke를 왜 usecase에서 사용을 하는지에 대해서 알아보겠다.

<br>

* invoke는 클래스의 인스턴스가 마치 함수인 것처럼 호출될 수 있게 하는 **특수 함수**이다. 주입 가능한 생성자를 써서 클래스를 함수로 변환

<br>

* invoke 연산자는 클린 아키텍처의 람다식 또는 usecase 객체 같은 함수를 나타내는 객체에 사용된다.

<br>

* 이점
    * 계약이 없는 usecase에 의사 계약 실행
    * 더 자연스럽게 읽힘
    * 호출의 유연성(loginUseCase() VS loginUseCase.invoke()) 