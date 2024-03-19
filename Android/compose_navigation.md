# android -> Jetpack Compose Navigation

<br>

* Android Jetpack Compose Navigation의 구성요소 3가지

    * NavController     
        * 대상 -> 앱 화면 간의 이동을 담당한다
        * Navigation 구성요소의 중심 api로, 스테이트풀이며 앱의 화면과 각 화면 상태를 구성하는 컴포저블의 백 스택을 추적
        * 컴포즈 환경에서 NavControler는 rememberNavController()를 이용하여 가져올 수 있다
        * 위를 사용해서 NavController 인스턴스를 생성할 때 유의해야 할 점은 상태호스팅에 유의해야 한다.
        * 컴포저블 계층 구조에서 NavController를 만드는 위치는 이를 참조해야 하는 모든 컴포저블이 액세스할 수 있는 곳이어야 한다.

        <br>

    * NavHost       
        * 이동할 컴포저블 대상을 매핑하는 것을 담당
        * 자체 포함된 탐색이 발생할 수 있도록 컴포즈 계층 구조에 제공한다
        * 지정된 NavGraphBuilder 내의 모든 컴포저블을 제공된 navController에서 탐색할 수 있다 -> 각 NavController를 단일 NavHost 컴포저블과 연결해야 한다
        * 내부적으로 구성 가능한 대상을 지정하는 NavGraph와 NavController를 연결한다
        * 이 연결을 통해 NavController는 이동한 컴포저블 대상을 파악하고 이동을 할 수 있게 된다

        <br>

        * e.x -> 

            -navController: NavHostController 클래스의 인스턴스이고, navigate() 메서드를 호출하여 다른 대상으로 이동하는 등의 방식으로 화면 간에 이동하는 데 이 객체를 사용할 수 있다

            -startDestination: 앱에서 NavHost를 처음 표시할 때 기본적으로 표시되는 대상을 정의하는 문자열 경로이다

            -builder: NavGraphBuilder로 그래프를 생성하기 위해 사용되는 빌더이고, 여기에 NavGraphBuilder의 composable() 함수를 이용하여 경로 대상을 정의 할 수 있다.


            ```kt
            public fun NavHost(
                navController: NavHostController,
                startDestination: String,
                modifier: Modifier = Modifier,
                route: String? = null,
                builder: NavGraphBuilder.() -> Unit
            )
            ```
        <br>

    * NavGraph       
        * NavGraph의 현재 대상을 표시하는 컨테이너 역할을 하는 컴포저블
        * ID로 가져올 수 있는 NavDestination 노드의 집합이다
        * NavGraph는 '가상' 대상 역할을 한다
        * NavGraph 자체는 백 스택에서 나타나지 않지만 NavGraph로 이동하면 시작 대상이 백 스택에 추가된다
        * 새로운 NavGraph는 대상을 추가하고 시작 경로를 설정할 때까지 유효하지 않다
        * 대상을 추가하는 방법은 NavGraphBuilder.composable() 함수를 이용한다

<br>

* * *

<br>

이상이다...