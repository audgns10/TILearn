# Android -> JWT Android Overview

<br>

* AuthInterceptor : OkHttp3의 Interceptor 상속   

    request 헤더에 JWT 토큰을 추가해주는 작업함   
    response 헤더에 Authorization 키 값이 존재하면 Access Token을 업데이트함

<br>

* AuthAuthenticator : OkHttp3의 Authenticator 상속   

    401 http error code를 받았을 상황에 호출되는 클래스   
    Access Token이 만료시 Access Token을 Refresh Token으로 바꾸고 API를 요청함

<br>

* TokenManager : Token DataStore-Preferences  

    Access Token을 로컬에 저장을 함   
    토큰 CRUD 작업 동기 or 비동기로 선택을 해서 작업이 가능

<br>

* * *

<br>

* Interceptor   
    Interceptor는 HTTP 통신을 모니터링 할 수 있게 해준다, API 재요청이 가능하게 해준다. Interceptor에는 종류가 두가지가 있다.   

    * Application Interceptor   
        주로 어플리케이션의 비즈니스 로직과 관련된 작업을 할 때 사용된다   
        네트워크의 호출 이전에 수헹이 된다   
        사용자 인증 토큰 추가, 캐시 구현 등의 구현 예시가 있다

    <br>

    * Network Interceptor   
        네트워크 요청 및 응답과 관련된 작업을 수행하는데 사용된다   
        네트워크 요청 및 응답로그 등의 구현 예시가 있다