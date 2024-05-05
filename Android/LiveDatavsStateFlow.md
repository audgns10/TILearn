# Android -> LiveData vs StateFlow

* 일단 livedata와 stateflow는 비슷한 점이 많다. / 둘 다 관찰 가능한 data holder class를 가지고 있고, 앱 아키텍처에 사용할 때 비슷한 패턴을 따른다.

* 다른점 
    * livedata
        * android 플랫폼에 종속적이다
        * 생명주기를 가진 Activity, Fragment 등을 관찰하고, 관찰 대상의 생명주기에 따라 데이터를 전달한다.(뷰가 STOPPED 상태가 되면 LiveData.observe()는 소비자를 자동으로 등록 취소)

    * stateflow
        * 순수 kotlin 라이브러리이다
        * 안드로이드 생명주기를 모른다.(뷰가 STOPPED 상태가 되어도자동으로 수집을 중지하지 않음) 동일한 동작을 하려면 **Lifecycle.repeatOnLifecycle** 블록에서 흐름을 수집해야한다

    * Guide
        * android 생명주기와의 통합이 중요한 경우 -> livedata
        * flow 라이브러리를 사용하고 싶은 경우 -> stateflow

    * **clean architecture의 관점에서는 livedata보다는 stateflow를 사용하는 것이 나을 것이다**

    * stateflow 정리
        * 현재 상태와 새로운 상태 업데이트를 수집기에 내보내는 관찰 가능한 상태 홀더 
        * value를 통해서 현재 값의 상태를 읽을 수 있음
        * 상태를 업데이트하고 흐름에 전송을 하려면 MutableStateFlow 클래스의 value에 새 값 할당
        * hot stream : StateFlow에서 수집되는 모든 클래스가 소비자 (flow 는 cold stream : 하나의 소비자에게 전송)
        * LiveData와 다르게 생명주기가 Destroy 될 때 까지 데이터를 수집한다. 그래서 뷰가 표시되지 않을 때 또는 앱이 백그라운드에 있을 때도 데이터를 수집하여 메모리 문제를 발생시켜 앱이 다운될 수 있다. 이를 방지하기 위해서는 repeatOnLifecycle API를 사용하여야한다. 하지만! 백그라운드에서도 수행되어야 하는 작업은 repeatOnLifecycle을 사용하면 안된다.