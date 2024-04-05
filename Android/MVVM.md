# Android -> MVVM 디자인 패턴

<br>

* M -> Model   
    애플리케이션의 데이터와 비즈니스로직을 담당한다

* V -> View   
    화면을 나타내는 뷰(ui)

* V -> ViewModel   
    view에 필요한 데이터를 model에서 viewmodel로 가져와서 처리를 하고 해당 데이터를 view에 업데이트를 해준다

<br>

* * *

<br>

* 흐름도   
    사용자가 view에서 이벤트를 발생시키고, 사용자의 이벤트의 데이터를 viewmodel에 데이터를 넘겨준다. 그리고 또 해당 데이터를 model에 넘겨준다. mode과 viewmodel이 서로 상호작용을 한다. 그리고 viewmodel에서는 livedata(?)을 통해서 옵저빙을 한 다음, 해당 데이터를 view에 전달을 한다(변경 사항이 있을때 view update)