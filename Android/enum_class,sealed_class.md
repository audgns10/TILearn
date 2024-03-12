# Android -> enum class VS sealed class

## enum class ->

* enum의 한국어 뜯은 열거형이고, 연관이 있거나 관련이 있는 상수들의 집합을 표현할 때 자주 사용을 한다.

* 인스턴스의 생성과 상속을 방지하여 타입 안전성을 보장한다

* 예시 코드, 문제점
    ```kt
    fun main() {
        val list = listOf<EnumCafe>(EnumCafe.Americano, EnumCafe.Latte, EnumCafe.Frappe, EnumCafe.IceTea)

        for(item in list) {
            val result = when(item) {
                EnumCafe.Americano -> '아메리카노',
                EnumCafe.Latte -> '라떼',
                EnumCafe.Frappe -> '프라페',
                EnumCafe.IceTea -> '아이스티'
            }
            println(result)
        }
    }

    enum class EnumCafe(val price: Int, val menunumber: String, val sugar: Int) {
        Americano(3500, "아이스아메리카노", 10),
        Latte(4000, "아이스라데", 25),
        Frappe(5000, "프라페치노", 100),
        IceTea(4500, "아이스티", 50)
    }
    ```
    * 속성값들을 바꾸는 것에 제약이 따른다
    * 설탕 인자가 없는 별도의 인자를 만들 수 없음
    * 이벤트 인자가 들어간 새로운 메뉴를 넣을 때도 제약이 따른다

## sealed class ->

* enum class의 제약사항을 해결이 가능하다. 왜? 추상 클래스 이면서 자신을 상속받는 여러 서브 클래스를 생성할 수 있다

* 예시 코드
    ```kt
    fun main() {

    val list = listOf<SealedCafe>(
        SealedCafe.Americano(500, "아메리카노", true),
        SealedCafe.Latte(500, "아메리카노"),
        SealedCafe.Frappe(500, "아메리카노", "사과"),
        SealedCafe.IceTea(500, "아메리카노", 100)
    )

        for (item in list) {

            val result = when (item) {
                is SealedCafe.Americano -> "아메리카노"
                is SealedCafe.Latte -> "라떼"
                is SealedCafe.Frappe -> "프라페"
                is SealedCafe.IceTea -> "아이스티"
            }

            println(result)
        }
    }

    sealed class SealedCafe {
        data class Americano(val price: Int, val menuName: String, val 디카페인: Boolean) : SealedCafe()
        data class Latte(val price: Int, val menuName: String) : SealedCafe()
        data class Frappe(val price: Int, val menuName: String, val fruit: String) : SealedCafe()
        data class IceTea(val price: Int, val menuName: String, val ice: Int) : SealedCafe()
    }
    ```

    * 속성값을 변동적으로 사용이 가능함
    * 이종의 클래스들을 혼합해서 사용이 가능하다
    * when 절을 사용할 때는 is Type을 사용해서 체크를 하면 된다