# gitFlow

## Git Flow란?

* 브랜치를 나누는 방법에 대한 분류 중 하나이다
* Git Flow의 특징은 브랜치가 5가지로 나뉜다는 것이다
    * main(master) : 서비스을 직접 배포하는 역할을 하는 브랜치이다
    * feature(기능) : 각 기능 별 개발 브랜치이다
    * develop(개발) : feature에서 개발된 내용이 저장되는 브랜치이다
    * release(배포) : 배포를 하기 전 내용을 품질 검사하기 위한 브랜치이다
    * hotfix(빨리 고치기) : main 브랜치로 배포를 하고 나서 버그가 생겼을 때 빨리 고치기 위한 브랜치이다

* main, develop은 필수 브랜치이지만 나머지 브랜치는 유지 보수를 목적으로 하는 옵셔널한 브랜치이다

![텍스트](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FsrKG9%2Fbtr2uggNS5A%2FOK72LJEGZtsKKW8FC5lCS1%2Fimg.png)