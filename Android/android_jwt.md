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