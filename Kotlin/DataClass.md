# Kotlin -> DataClass

## DataClass

* 데이터 클래스는 일반 클래스와 달리 다양한 메소드를 자동으로 생성해주는 클래스이다
* 데이터 클래스 생성 시 같이 만들어지는 것들
    * hashCode()
    * copy()
    * equals()
    * toString()
    * componentsN()
    
    * 특징
        * 기본 생성자에 1개 이상의 파라미터가 있어야함
        * 기본 생성자 파라미터가 val 또는 var로 선언해야함
        * 다른 클래스를 상속받을 수 없음(수퍼 클래스를 가지는것이 불가능) 하지만 sealed 클래스는 상속받을 수 있고, 인터페이스는 구현할 수 있음
        * abstract, open, sealed, inner 등 키워드를 붙일 수 없음
        * 자동으로 생성한 메소드를 오버라이딩할 경우 , 오버라이드 된 메소드 사용

    1. toString() 메소드
        * 생성한 객체를 고대로 출력해보면 갖고 있는 프로퍼티의 값들이 알아서 출력되는 것을 확인이 가능하다
        * toString()이 구현되어있기 때문이다. 디버깅 시 로그캣을 통해 매우 편리하게 사용할 수 있다
        * 메소드를 자동으로 생성해주는 것이 높은 장점이다

    2. copy() 메소드
        * copy() 메소드는 특정 필드값만 바꿔서 복사하기에 간편하다

    3. hashCode() 메소드
        * 프로퍼티 값이 완전 같은 두 DataClass 객체를 만들고 hashCode()를 출력하면 -> 두 객체의 hashCode()가 같은 값을 출력함을 확인할 수 있다. 일반 클래스라면 다른 값을 가지게 된다

    4. equals() 메소드
        * '==' 연산자 하나로, 두 객체가 동일한 값을 담고있는지 쉽게 검사가 가능함
        * '===' 연산도 가능함 하지만 메모리 상 다른 객체이므로 false가 출력됨
        * 갖고 있는 값이 동일한지 검사 -> '==' / 메모리상 같은 객체인지 검사 -> '==='

    5. componentN() 메소드
        * Data Class는 기본적으로 componentN() 메소드가 생성이 되기 때문에, 각  프로퍼티에 번호가 붙어 구조 분해가 가능한 형태가 됨
        * 프로퍼티가 2개이고, 이 때 선어 순서가 name 다음에 age 형태로 되어있기 때문에 compoent1() 메소드에 name 필드가 대응되고 component2() 메소드에 age 필드가 대응된다

    ![텍스트](https://media.discordapp.net/attachments/1159414048518045696/1161821828830986330/image.png?ex=6539b1e5&is=65273ce5&hm=88975d2d86b0b25eae280682a6ddf9fcec52da35380845d51d1d29dfac365b09&=&width=717&height=1002)