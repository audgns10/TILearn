# android -> StateFlow

내가 블로그로 viewmodel를 공부를 하면서 여러 코드들을 봤다. 그런데 coroutine의 Flow와 StateFlow를 사용을 하는 것이였다.

나는 LiveData라는 것을 알고 있고 그것을 사용을 하려 했지만 내가 사용을 하는 clean architecture에서는 LiveData 보다는 StateFlow를 사용을 하는 것이 더 좋다고 하는 블로그들을 여러개를 보고 여러 프로젝트의 코드들을 봐도 그런 것 같았다.

간단하게 개념을 설명을 하면 -> 

StateFlow -> hot stream -> StateFlow에서 수집되는 모든 클래스가 소비자   
        * 그냥 Flow도 있지만 그냥 Flow는 cold stream이다. 왜냐하면 하나의 소비자에게 전송을 하기 떄문이다.

    * 생명주기가 파괴가 될 때 까지 데이터를 수집한다. 그래서 뷰가 표시가 안되거나 앱이 백그라운드에 있어도 문제가 되지 않음
    
    * 동일한 동작을 하려면 repeatOnLifecycle 블록에서 흐름을 수집을 해야한다.