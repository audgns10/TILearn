# Android -> DI(Hilt) -> 사용법

<br>

1. DIApp 클래스를 android:name 항목으로 연결을 합니다.

<br>

2. DIApp을 '@HiltAndroidApp'으로 어노테이션을 합니다.
    ```kt
    @HiltAndroidApp
    class DIApp : Application()
    ```

    *  의존성 주입을 하기 위해서는 Application이 있어야함.(초기화 코드가 있어야 하는데 그것이 @HiltAndroidApp이다)

<br>

3. Activity에 @AndroidEntryPoint를 넣어준다
    ```kt
    @AndroidEntryPoint
    class DiMainActivity : ComponentActivity() {
        ...
    }
    ```

    * @AndroidEntryPoint는 주입할 공간이라고 보면 된다.(외부에서 주입한 것을 여기에 넣겠다)

<br>

4. 대입을 해주어야 하는 곳을 만들어야함 -> Module에 '@Module' 어노테이션과 '@InstallIn(SingletonComponent::class)' 어노테이션이 추가한다.
    ```kt
    @InstallIn(singletonComponent::class)
    @Module
    ...
    ```

    * @Module은 의존성 주입을 하고 있는 프로바이더가 있는 공간이라고 보면된다.
    * @InstallIn 싱글톤을 할 애들은 여기다가 설치를 해달라고 하는 것이라고 보면된다.(이렇게 컴포넌트가 만들어져있어서 자동으로 연결을 해주는 것이다.)
    
<br>

5. @Provides를 만들어준다.
    ```kt
    @Singleton
    @Provides
    @Named("DI_URl")
    fun provideApi() : String = "https://___"
    ...
    ```

    * @Singleton은 한번만 생성되게 하겠다는 것이라고 보면된다.
    * @Provides 여기에다가 주입을 해야하기 때문에 쓰인다.
    * @Named는 스트링이 여러 개일 수도 있다 -> 어떤 타입이 있는지만 확인을 하는데 같은 타입이 여러 개일 수도 있기 때문에 이러한 경우에는 @Name 세팅해준다

<br>

6. HiltViewModel를 사용할때 -> @HiltViewModel 어노테이션을 지정을 한다. / 생성자에 @Inject(뒤에 constructor)를 붙여준다
    ```kt
    @HiltViewModel
    class ExViewModel @Inject constructor(
        private val exService: ExService
        ...
    ) : ViewModel() {
        ...
    }
    ```

    * 액티비티를 쓸 수 있게 하기 위해서 @HiltViewModel을 설정을 한다.(의존성 주입의 문제도 해결이 되고, 다른 곳에서 가져다가 쓰는 것도 해결이 된다)
    * @Inject를 써줘야 하는데 그냥 혼자서는 못쓰기 때문에 앞에 constructor를 붙여준다.