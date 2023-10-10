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

* * *

![텍스트](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FsrKG9%2Fbtr2uggNS5A%2FOK72LJEGZtsKKW8FC5lCS1%2Fimg.png)

1. master 브랜치로 시작을 한다
2. 동일한 브랜치를 develop에도 생성을 한다. 개발자들은 이 develop 브랜치에서 개발을 진행한다
3. 개발을 진행하다가 회원가입, 장바구니 등의 기능 구현이 필요할 경우 A개발자는 develop 브랜치에서 feature 브랜치를 하나 생성해서 회원가입 기능을 구현하고 B개발자도 develop 브랜치에서 feature 브랜치를 하나 생성해서 장바구니 기능을 구현한다
4. 완료된 feature 브랜치는 검토를 거쳐 다시 develop 브랜치에 합친다(merge)
5. 이제 모든 기능이 완료되면 develop 브랜치를 releaes 브랜치로 만든다. 그리고 품질검사를 하면서 보완점을 보완하고 버그를 고친다
6. 모든 기능이 완료되면 release 브랜치를 master 브랜치와 develop 브랜치로 보낸다. master 브랜치에서 버전추가를 위해 태그를 하나 생성하고 배포를 한다
7. 배포를 했는데 미처 발견하지 못한 버그가 있을 경우 hotfixes 브랜치를 만들어 긴급 수정 후 태그를 생성하고 바로 수정 배포를 한다