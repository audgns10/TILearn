# android -> clean architecture

![Alt text](image.png)

* 의존성 ->   
**presentaion -> domain / data -> domain**

* presentation
    * view
    * viewModel

    <br>

* domain
    * usecase -> 바로 repository를 viewmodel에서 사용을 할 수도 있지만 invoke를 사용해서 usecase를 구성하고 viewmodel에서 usecase를 사용한다면 파라미터로 받을 수 있기 때문에 유지보수나 협업에서의 측면에서 긍정적인 효과를 볼 수 있음
    * repository

    <br>

* data
    * repositoryImpl
    * data source
    * dto
    * server api interface
    * mapper

<br>
<br>

**내용이 좀 부실해요**