# Android -> UiState

<br>

**DataLayer로 부터 데이터를 받아오게 되고, 그 데이터들과 함께 게시물이 보여지게 되는 것이다. -> 이때 UI에 해당 개시물이 보여지게 된는 것이고, 앱에서 사용자에게 표시하는 정보가 UiState이다**

**사용자가 보는 항목이면 UI, 사용자가 봐야한다고 지정하는 것은 UiState이다**

<br>

* Android에서는 UiState를 사용하기 위ㅎ서 sealed class를 활용한 State Modeling 전략을 사용한다