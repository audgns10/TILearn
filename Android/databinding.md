# Android --> data binding


## data binding

*data binding은 제공자와 소비자로부터 데이터 소스를 함께 묶어 동기화하는 일반적인 기법이다.*

* 이것은 보통 XML 데이터 바인딩과 UI 데이터 바인딩에서와 같이 서로 다른 언어를 사용하는 두 개의 데이터 정보 소스로 이루어진다. UI 데이터 바인딩에서는 언어와 다른 로직 함수의 데이터 및 정보 객체가 서로 결합된다(EX_ Java UI 요소와 Java 객체)

<br>

### 안드로이드에서의 data binding

*안드로이드에서의 databinding이란 Android Archictecture Components의 한 부분으로서 UI 요소와 데이터를 프로그램적 방식으로 연결하지 않고, 선언적 형식으로 결합할 수 있게 도와주는 라이브러리를 말한다*

<br>

### data binding을 사용하는 이유

*데이터 바인딩을 사용하면, 데이터를 UI 요소에 연결하기 위해 필요한 코드를 최소화할 수 있다*

* 장점

    1. findViewld()를 호출하지 않아도, 자동으로 xml에 있는 View들을 만들어준다
    2. RecyclerView에 각각의 item을 set 해주는 작업도 자동으로 진행된다
    3. data가 바뀌면 자동으로 View를 변경하게 할 수 있다
    4. xml 리소스만 보고도 View에 어떤 데이터가 들어가는지 파악이 가능하다
    5. 코드 가독성이 좋아지고, 상대적으로 코드량이 줄어든다

* 하지만 클래스 파일이 많이 생기고 빌드의 속도가 느려지는 등 단점들도 존재한다
    * 그래서 data binding은 data binding 단독으로만 사용하는 것보다 MVVM 또는 MVP 아키텍처와 함께 사용해야 빛을 발한다는 것이 업계의 오피셜이다

<br>

### data binding을 사용하는 방법

1. app/build.gradle에 dataBindind 요소를 추가한다

    <br>

    ![텍스트](https://media.discordapp.net/attachments/1171055198978977792/1172064888366055464/image.png?ex=655ef57d&is=654c807d&hm=d7ae240554a5b4966a01faca33d2cc9b0ff28809ab9632dbd529fe921011e34d&=&width=519&height=211)

    <br>
    <br>

2. <layout> 태그 안에 XML 레이아웃을 작성한다
    * data binding을 사용하는 xml 리소스는 <layout> 루트 태그로 시작하여야 한다

    <br>

    ![텍스트](https://cdn.discordapp.com/attachments/1171055198978977792/1172066628083654696/image.png?ex=655ef71c&is=654c821c&hm=da1a1628498e40eba85ca6c203254d0302b413466a53ff5a775de9efbfe525fc&)

    * binding class는 data binding을 사용하는 클래스의 이름에 따라 각 레이아웃 파일에 대해 뒤에 "Binding" 이라는 suffix가 붙은 Camel Case로 자동으로 생성된다

    * 즉, 위 코드의 activity_main_xml에 대해 자동 생성된 binding class의 이름은 MainActivityBinding이다

    <br>
    <br>

3. Activity에서 기존의 setContentView() 함수를 DataBindingUtil.setContentView()로 교체한다

    * DataBindingUtil class의 객체를 생성하고, 기존의 setContentView()를 DataBindingUtil.setContentView()로 대체한다

    <br>

    ![텍스트](https://cdn.discordapp.com/attachments/1171055198978977792/1172068552057045023/image.png?ex=655ef8e6&is=654c83e6&hm=f3d99116e9fae057a38ceed411500c060e730e47975680d785a35beff0aa7f2c&)

    <br>
    <br>

4. View에 보여줄 이름 data class를 선언한다

    * data 객체를 view와 bind하기 위해서, User라는 이름의 data class를 하나 만들어준다

    <br>

    ![](https://cdn.discordapp.com/attachments/1171055198978977792/1172069524900679680/image.png?ex=655ef9ce&is=654c84ce&hm=09947364bbf3377d11826756afb91ee7218a2e8b48ffb0df6b05556c4cfa045d&)

    <br>
    <br>

5. xml 리소스의 <layout> 태그 안에 <data> 요소를 작성한다

    * <data> 태그는 <layout>에서 사용할 변수를 정의하는데 사용된다
    
    * User라는 객체를 사용할 것이기 때문에 name이 user인 variable을 하나 선언해 주었다

    * 레이아웃 내의 표현식은 "@{}" 구문을 사용하여 속성에서 작성된다

    <br>

    ![](https://cdn.discordapp.com/attachments/1171055198978977792/1172071557472989184/image.png?ex=655efbb3&is=654c86b3&hm=923f093066150feb9a9b0efcbc271f84dad98da5b92e3a32e0b02271773e7156&)

    <br>
    <br>

6. Activity에서 User 객체를 초기화 한다

    * User 객체를 초기화하여 binding 객체의 datasource를 set 해주도록 한다

    <br>

    ![](https://cdn.discordapp.com/attachments/1171055198978977792/1172072276817104958/image.png?ex=655efc5e&is=654c875e&hm=13e506e738a1e6776f964cbe93f8ecdd7bdaf921e11ee805d703241fad19c600&)