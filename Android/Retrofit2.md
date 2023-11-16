# Android --> Retrofit2

## Retrofit2란?

* API 통신을 위해 구현된 OkHTTP의 HTTP 통신을 간편하게 만들어주는 라이브러리를 뜻함
* Async Task가 없이 Background 쓰레드를 실행 -> CallBack을 통하여 Main Thread에서 UI를 업데이트
* 동일 Squareup사의 OkHttp 라이브러리의 상위 구현체

<br>

## 장점 3가지

* Retrofit2의 장점은 3가지로 볼 수 있음 -> (속도, 편의성, 가독성)
    * OkHTTP 사용 시에 AsyncTask를 통해 비동기로 실행하여 속도가 느린이슈. 하지만 Retrofit2에서는 자체적 비동기 실행과 스레드 관리가 가능하여 속도가 빠르다는 장점이 있다
    * 함수 호출 시에 파라미터를 넘겨주어 작업량이 감소
    * Interface 내에서 어노테이션을 사용하여 호출 함수를 미리 지정. 구현 없이 해당 함수를 호출만 해주면 되기 때문에 코드를 읽기에 매우 편하다. 또한 콜백 함수를 통한 직관적 설계가 가능
    * 동기 / 비동기 쉬운 구현
        * 동기 Synchronous -> 동시에 일어난다는 의미. 요청 - 응담이 하나의 트랜잭션에서 발생한다
        * 비동기 Asynchronous -> 동시에 일어나지 않는다는 뜻. 요청 - 응답은 별개의 트랜잭션. 요청 후 응답이 도착하면 Callback으로 받아서 처리

<br>

## 구성요소 3가지

* DTO(POJO) -> 'Data Transfer Object', 'Plain Old Java Object' 형태의 모덴 / JSON 타입변환에 사용
* Interface -> 사용할 HTTP CRUD동작들을 정의해놓는 인터페이스
    * CRUD -> HTTP Method(POST / GET / PUT / DELETE)
* Retrofit.Builder 클래스 -> Interface를 사용할 인스턴스, BaseUrl(URL) / Converter(변환기) 설정