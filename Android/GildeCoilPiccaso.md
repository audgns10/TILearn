# Android --> 이미지 로딩 관련 라이브러리

* Gilde
* Coil
* Piccaso

## Piccaso

* MinSdkVersion = 14
* CompileSdkVersion = 29
* Library Size = 121Kb
* GIF 지원 (x)

<br>

* Square 에서 만든 Picasso는 최소한의 메모리로 이미지의 다양한 Trasformation을 지원하며, 자동으로 메모리, 디스크 캐싱, 어댑터에서 ImageView를 재활용 및 다운로드 취소가 가능하다는 점을 강조함

* Picasso는 원본 이미지 크기를 그대로 비트맵에 그린 후에 이미지뷰에 적용한다

* 고화질의 이미지를 로드한다면 OOM을 발생시킬 수 있다

* 위같은 문제를 방지하기 위해 fit() 함수를 이용한다면 고화질 이미지를 로드하기 전 이미지뷰의 크기를 먼저 측정하기 때문에 사용량을 최소화할 수 있을 것이다

<br>

## Gilde

* MinSdkVersion = 14
* CompilSdkVersion = 26
* Library Size : 440Kd
* GIF 지원 (o)

<br>

* Google에서 만든 이미지 로더 라이브러리인 Gilde는 빠른 이미지 로딩, 버벅 거림과 끊김 현상이 발생하지 않는다는 점을 강조하고 있다

* 커스텀된 HttpUrlConnection을 사용하짐나 Villey 또는 OkHttp 라이브러리에 연결할 수 있는 유틸리티 라이브러리도 포함되어있어, 우리가 자주 사용하고 있는 라이브러리와 호활성이 좋다

* Gilde는 아래처럼 싱글톤으로 만들어 간단하게 사용이 가능하다

<br>

## Coil

* MinSdkVersion = 14
* CompileSdkVersion = 30
* GIF 지원 (o)

<br>

* Instracart에서 만든 Coil은 Coroutine Image Loading의 줄임말로 위에 설명했던 이미지로더 라이브러리와 달리 코틀린, 코루틴으로 구성이 되어있다

* 장점으로는 라이브러리가 거의 100% 코틀린으로 이루어졌다는 점과 AndroidX, OkHttp 등 현업에서 많이 쓰이고있는 라이브러리들을 지원하고 있다는 점이다

* Coil 라이브러리 내부를 살펴보면, Gilde와 굉장히 비슷하다는 것을 알 수 있는데 Gilde를 많이 벤치마킹 했다고 한다

* 또한 ImageView의 화강함수로 지원하고, 코틀린의 매력인 함수형 언어 덕으로 다른 라이브러리보다 더욱 간결한 코드를 구성할 수 있다