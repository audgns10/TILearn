# Android -> Linear Layout

* Linear Layout

## Linear Layout

* 화면에 보이는 구성 요소들은 모두 뷰라고 부른다 -> 우리가 흔히 보는 Button, TextBox, Image 등은 모두 뷰라고 부른다. 이러한 구성 요소들이 모여 하나의 화면을 이루게 됨

* 뷰를 화면에 배치할 수 있는 무언가가 필요하며 그 역할을 하는 것이 뷰 그룹 또는 뷰 컨테이너이다 -> 뷰 그룹은 연관된 여러 개의 뷰를 포함할 수 있으며 1개의 뷰는 반드시 하나의 뷰 그룹에 포함되어야 한다

* 안드로이드에서는 뷰 그룹을 상속받는 여러 가지 레이아웃 클래스를 제공하고 있다

<br>

1. Linear Layout

* Linear Layout은 뷰를 수평 또는 수직 방햑으로 배치할 수 있는 레이아웃이다 -> orientation 속성을 통해 배치방향을 결정할 수 있다

<br>

```
android:orientation = "vertical" -> 하위 뷰들을 수직방향으로 배치
```

```
android:orientation = "horizontal" -> 하위 뷰들을 수평방향으로 배치
```

<br>

2. gravity 속성과 layout_gravity 속성 차이

* gravity 속성은 모든 하위 뷰에 대한 배치방향을 결정
* layout_gravity 속성은 그룹 뷰에 속하는 하위 뷰들이 가지는 속성으로 뷰 그룹의 gravity 속성에 의해서 결정된 원래 자기 자신의 위치에서의 중력 방향을 결정하는 속성

<br>

3. layout_weight 속성

* 자식 뷰에 가중치를 지정해서 그 비율만큼 자식 뷰의 크기를 지정하는 속성

<br>

4. ViewGroup 안에 ViewGroup 포함하기

* 뷰 그룹 안에 뷰 그룹이 포함 되는것이 가능하다
* 뷰 취급을 하는것이다 -> 다른 말로 LinearLayout 안에 LinearLayout을 포함할 수 있다는 것
