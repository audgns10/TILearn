# Android -> JWT 그리고 세부적인 부분 / Access, Refresh token

<br>

* Header   
    alg : Signature에 사용하는 알고리즘   
    typ : 토큰 타입   

    **Signature에서 사용하는 알고리즘은 대표적으로 RS256(공개키/개인키)와 HS256(비밀키(대칭키))가 있다.**

<br>

* Payload   
    sub : 토큰의 제목
    aud : 토큰의 대상자
    iat : 토큰이 발급된 시간
    exp : 토큰이 만료된 시간
 
    **사용자의 정보의 한 조각인 클레임(claim)이 들어가 있다**

<br>

* Signature   
    Signature는 헤더와 페이로드의 문자열을 가져와서 둘이 합친후에, 헤더에 선언한 알고리즘과 key 값으로 암호화를 한 값이다.

    <br>

    **여기서 알게된점은 Header와 Payload는 알기 쉽기 때문에 중요한 정보를 담으면 안된다는 사실이다**

<br>

* * *

<br>

**장점, 단점 및 결론**

* 장점    
    로컬에 저장을 하기 때문에 서버 용량에 영향을 미치지 않는다   
    안전성이 보장된다    
    네트워크 부하가 적다    
    앱에서 사용하기 좋다(**android**, ios)

<br>

* 단점  
    토큰의 크기가 커질수록 트래픽에 영향을 미친다   
    트큰을 발급 받으면 토큰이 만료기간이 변경이 불가능해 토큰이 만료 되었을때 상황까지 생각을 해서 구현을 해야한다

<br>

# 정리

* 구조   
    Header : 서명 알고리즘(공개키/개인키, 비밀키)
    Payload : 토큰 정보(제목, 대상자, 만료시간, 발급시간)
    Signature : (Header + Payload) 서명 (인증용)

<br>

* 장점   
    네트워크 부하가 적다 / 모바일 앱에서 사용하기 적합하다

<br>

* 단점   
    토큰의 크기를 생각해야한다 / 만료 기간도 생각해서 구현을 해야한다

* * *

**Access, Refresh Token**

* 문제   
    만약에 토큰을 탈취를 당했다면 토큰을 탈취한 사람은 마치 신뢰가 가능한 사람이 것처럼 사용이 가능하기 때문이다. 본 주인은 클라이언트와 탈취한 사람을 구분할 수 없다. -> 해결을 할 수 있는 방안은 유효기간을 두어야 하는 것이다.(Access, Refresh Token 두개를 두는 것이다)

    * Access Token의 기간은 짧다
    * Refresh Token의 기간은 길다
    * 평소 api 통신을 할때는 Access Token을 사용해서 하고 만로가 되었을때는 Refresh Token를 사용한다
    * Access Token의 기간을 짧게 두고 Refresh Token 자주 발급해주면서 피해를 최소화

<br>

* 프로세스   
    1. 로그인 인증에 성공한 클라이언트는 Access, Refresh Token를 받아온다
    2. 클라이언트는 Access, Refresh Token을 로컬에 저장을 해논다
    3. 클라이언트는 헤더에 Access Token을 넣고 API 통신한다
    4. 일정 시간이 지나 Access Token이 만료가 된다
        * Access Token은 이제 유효하지 않으므로 권한이 없는 사용자가 된다
        * 유효기간이 지난 Access Token을 받은 서버는 401를 반환한다
        * 401를 통해서 클라이언트는 만료가 되었음을 알 수 있다(invalid_token)
    5. 헤더에 Access Token 대신 Refresh Token를 넣어 API를 요청한다
    6. Refresh Token으로 사용자의 권한을 확인한 서버는 응답쿼리 헤더에 새로운 Access Token을 넣어 응답을 해준다
    7. 만약 Refresh Token이 만료가 된 경우라면 401를 뱉고, 클라이언트는 재로그인을 시도해야한다

    **이런식으로 한다면 Access Token을 탈취한다고 해도 기간이 짧기 때문에 다른 Access Token을 다시 탈취를 해야할 것이다.. 왜냐하면?! JWT Token은 만료시간을 변경하는 것이 불가능!!하기 때문이다.**

    * Refresh Token의 탈취 위험성(Refresh Token Rotation으로 해결)
        * Refresh Token의 통신 빈도가 적기는 하지만 아예 안위험하다고 말을 할 수는 없다. 이에 대한 해결 방안으로는 Access Token을 받아올때 Refresh Token도 새로 받아오는 방법이다 -> 만약 이렇게 된다면 탈취가 Refresh Token을 탈취를 하였다고 하더라도 그것이 유효기간이 더이상 길지않은 Refresh Token 일것이다.