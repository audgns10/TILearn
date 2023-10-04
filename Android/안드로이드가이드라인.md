# Android --> Guideline

## Guideline

* 가이드라인은 말그대로 레이아웃 작성시에 가이드라인을 잡아주는 역할을 한다 --> 화면 내에서 가상의 선을 하나 그어, 해당 선에 view들의 constraint를 줄 수 있게 도와주는 역할이다

* 예시

```xml
<androidx.constraintlayout.widget.Guideline
    android:id="@+id/guideline"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:orientation="vertical"
    app:layout_constraintGuide_begin="24dp" />
```

![텍스트](https://velog.velcdn.com/images%2Fwooyoung-tom%2Fpost%2Ff30186a1-cb6f-4069-bcb1-0cf236d4d493%2Fguideline_1.png)

* * *

* android:id --> 해당 가이드라인의 id
* android:layout_constraintGuide_xxx --> 가이드라인의 위치를 지정할 때 사용(vertical:수직_화면의 위쪽과 아래쪽이 시작과 끝 / horizontal:수평_화면의 왼쪽과 오른쪽이 시작과 끝)
* app:layout_constraintGuide_begin --> 화면의 시작으로부터 얼마만큼 떨어져있으면 좋겠는지 지정
* app:layout_constraintGuide_end --> 화면의 끝에서 얼마만큼 떨어져있는지를 정해줄 수 있음
* app:layout_constraintGuide_percent --> 화면의 시작을 0%, 화면의 끝을 100%로 생각하고 전체 화면에 대해 몊 퍼센트 위치에 있는지 정하는 것이 가능