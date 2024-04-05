# android -> ViewModel

<br>

**ViewModel은 두가지의 종류가 있다. MVVM 패턴에서 언급이 되는 ViewModel과 테스트와 유지보수를 용이하게 하게 할 수 있는 AAC(Android Architecture Components) ViewModel이 있다**

<br>

* MVVM의 ViewModel  
    View와 Model 사이의 매개체 역할을 하고 View에 보여지는 데이터를 가공을 하게 된다

* ACC의 ViewModel   
    앱의 LifeCycle을 고려하여 UI 관련 데이터를 저장하고 가공을 한다

<br>

* * *

<br>

* 구글에서는 MVVM을 사용해서 앱을 만드는 것을 권장하고
* MVVM을 사용하여 구현을 할때 AAC ViewModel을 사용하여 구현을 하는 것이 좋다