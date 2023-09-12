# Android -> ConstraintLayout

* ConstraintLayout

## ConstraintLayout

1. ConstraintLayout이란?

* ConstraintLayout이란 부모 뷰그룹 안의 다른 요소들과의 상대적인 제약조건을 설정함으로써 화면에 배치되도록 하는 레이아웃을 말한다

2. ConstraintLayout 제약 유형

    * **Relative positioning(상대적 위치지정)** : 다른 요소와 수평, 수직방향의 상대적 배치를 위한 속성
    * **Margins(여백)** : 여백 설정을 위한 속성
    * **Centering positioning(중앙 위치지정)** : 중앙 배치를 위한 속성
    * **Circular positioning(원형 위치지정)** : 다른 요소와 원 형태의 상대적 배치를 위한 속성
    * **Visibility behavior(가시성 동작)** : visility 속성에 따른 동작 속성
    * **Dimension constraints(크기 제약)** : 뷰의 크기를 위한 속성
    * **Chains(연결)** : 수평 또는 수직방향으로 연결된 뷰를 위한 속성
    * **Virtual Helpers objects(가상의 도움 객체들)** : 뷰의 배치에 도움을 줄 수 있는 객체 속성
    * **Optimizer(최적화)** : 제약조건 최적화 속성

<br>

3. ConstraintLayout 제약 유형별 속성과 사용방법

    1. Relative positioning
        * ConstraintLayout에서 Relative positioning은 뷰를 배치하기 위해 기본적으로 사용되는 개념으로 다른 요소들과의 수평, 수직방향으로 일치시키기 위해 사용되는 속성이다

    <br>

    2. Margins
        * ConstraintLayout에서는 기본적인 margin 이외에 화면 배치를 위해 참조하던 요소가 화면에서 사라졌을 때의 상황을 고려한 margin을 지정해 줄 수 있다

    <br>

    3. Centering positioning
        * 중앙 정렬이 되도록 하기 위해서는 양쪽 방향으로 제약을 동시에 걸어주면 된다 -> 예를들어 수평방향으로의 가운데 정렬을 위해서는 아래 그림과 같이 왼쪽과 오른쪽에 제약을 동시에 걸어주면 된다 /  마찬가지로 수직방향으로의 가운데 정렬을 위해서는 위쪽과 아래쪽에 제약을 걸어주면 된다

        * bias는 한쪽 방향으로 치우친 정도를 나타내는 값 -> 0~1의 값을 가지며 defualt값인 0.5일 경우 중심에 위치하게 된다 / bias가 0.25일 경우에는 수평으로 25%의 지점에 위치하게 된다

    <br>

    4. Circular positioning
        * 뷰를 화면에 나타낼 때 다른 요소와 수평 또는 수직 형태의 상대적 위치 지정뿐 아니라 원형 형태로의 상대적 위치 지정을 할 수 있다 -> 이를 위해서는 다른 요소와 떨어진 각도와 거리 요소를 필요로 하게 된다

    5. Visibility behavior
        * visibility 속성은 다른 레이아웃과 동일하게 사용된다 -> 또한 위에서 살펴본 Margins와 관련된 속성을 참고하면 기준 뷰가 사라진 상태에서의 마진 값을 따로 정의할 수도 있다

    <br>

    6. Dimension constraint
        * 뷰의 width와 height는 다음 세 가지 방법으로 값을 정할 수 있다
            1. (방법1) 직접 크기 지정 : 직접 width와 height 값을 지정해 준다
            2. (방법2) wrap_content : 뷰에 포함된 내용의 크기에 따라 뷰의 크기가 자동으로 결정된다
            3. (방법3) match_constraint : 0dp를 입력하면 match_constraint로 제약조건에 부합되는 뷰의 크기를 가지게 된다(ConstraintLayout에 포함된 뷰에서는 match_parent 대신 match_constraint를 사용하도록 권장한다)

        * match_constraint를 사용했을 경우, width와 height의 최소, 최대값을 지정할 수 있다

        * match_constraint를 사용했을 경우, 부모 뷰그룹의크기에 비례하도록 설정할 수 있다

        * wrap_content를 사용했을 경우, width와 height의 최소, 최대값을 지정할 수 있다

        * 뷰의 width와 height의 비율로 크기를 나타낼 수도 있다

    <br>

    7. Chains
        * Chains은 수평 또는 수직 방향을 연결된 뷰를 그룹처럼 다룰 수 있다. 뷰들간에 양방향으로 연결되었을 때 체인으로 인식되며 체인은 첫번째 요소에 설정된 속성에 의해 제어된다 -> 체인의 연결 형태는 spread, spread_inside, packed 3가지가 있으며 defualt는 spread이다

        * 체인으로 연결된 뷰중에 match_constraint가 적용된 뷰가 있으면 해당 뷰가 여백 공간을 모두 차지하게 된다 / 두개 이상의 뷰가 match_constraint인 경우에는 weight를 이요하여 여백을 차지하는 비율을 지정할 수 있다

    <br>

    8. Virtual Helpers objects
        * ConstraintLayout에서는 화면에 나타나지는 않지만 홤녀 구성을 편리하게 도와주는 여러 객체들이 있다 / 이러한 객체로는 Guideline, Barrier, Group, Placeholder가 있다
            1. Guideline : 뷰의 위치를 지정하는데 도움을 주는 기준선
            2. Barrier : 장벽처럼 등록된 뷰들의 최외곽 경계를 나타내는 가상의 동적 기준선
            3. Group : 참조된 여러뷰들의 visibility를 한번에 제어할 수 있도록 그룹화한 객체
            4. Placeholder : 이미 존재하고 있는 뷰의 위치를 이동시켜 재배치 할 수 있는 객체

    <br>

    9. Optimizer
        * ConstraintLayout 요소에 layout_optimizationLevel 태그를 추가함으로 최적화 수준을 선택 할 수 있다