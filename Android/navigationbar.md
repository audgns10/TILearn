# navigation bar(fragment) -> android

<br>

## 만드는 순서

1. viewBinding을 사용하기 때문에 viewBinding 설정 추가
    ```
    buildFeatures {
        viewBinding = true
    }
    ```

<br>

2. Fragment를 사용해서 하단바를 만들기(Fragment 4개 추가), NaviActivity.kt 생성

    ![](https://cdn.discordapp.com/attachments/1173511176664121408/1177412227872079945/image.png?ex=65726996&is=655ff496&hm=509beffadfeade9bc59c83af465cde878628f3b8ee4326913982d803a4720ff6&)


<br>

3. drawable에서 navigation bar에 들어갈 Vector를 생성
 
    ![](https://cdn.discordapp.com/attachments/1173511176664121408/1177412642822955028/image.png?ex=657269f9&is=655ff4f9&hm=43e15969fd56b864408b3785aa5ed21ec219af1937967f9c0fcd88a88635fcdf&)

<br>

4. res에 menu를 생성하고, Menu Resource File을 생성(navi_menu.xml 파일 생성 후에, navigation bar 메뉴를 만들어줌)

    ![](https://cdn.discordapp.com/attachments/1173511176664121408/1177413319108349972/image.png?ex=65726a9a&is=655ff59a&hm=8bc3a43d5b33a8ba1a3894785724f4eb266f39b5a2d7c15285e6736cfc67abed&)

    ![](https://cdn.discordapp.com/attachments/1173511176664121408/1177413511018729542/image.png?ex=65726ac8&is=655ff5c8&hm=c1cf90dd13505623dfb25352f27974c488a055aa92099e3560114a316f5e23d9&)

<br>

5. color.xml에 하단 바에 들어갈 색상 설정을 추가

    * 나는 하얗게 만들고 싶었기 때문에 그냥 원래 설정이 되어있는 하얀색으로 함

<br>

6. 클릭시 색상을 변경하기 위한 drawable 추가

    ![](https://cdn.discordapp.com/attachments/1173511176664121408/1177414458377773167/image.png?ex=65726baa&is=655ff6aa&hm=89e2022f408fd7f16cca2fb1988371b7127ff49d0ff333ebd874f986af7b6264&)

<br>

7. activity_navi.xml 코드쓰기

    ![](https://cdn.discordapp.com/attachments/1173511176664121408/1177414796291878962/image.png?ex=65726bfa&is=655ff6fa&hm=e4e2339c66fdcdd096736ce8a4681109b9c994a0797429b9cf58f1afc4fa82bc&)

    ```xml
    app:itemActiveIndicatorStyle="@null"
    // 위 코드는 클릭이 되었을때 퍼져나가는 Ripple 효과를 없애기 위해 추가함
    ```

<br>

8. NaviActivity 코드쓰기

    ```kt
    package com.example.navigationbar

    import androidx.appcompat.app.AppCompatActivity
    import android.os.Bundle
    import androidx.fragment.app.Fragment
    import androidx.fragment.app.FragmentManager
    import com.example.navigationbar.databinding.ActivityNaviBinding

    private const val TAG_SEARCH = "search_fragment"
    private const val TAG_PIN = "pin_fragment"
    private const val TAG_HOME = "home_fragment"
    private const val TAG_MY_PAGE = "my_page_fragment"

    class NaviActivity : AppCompatActivity() {

        val binding by lazy { ActivityNaviBinding.inflate(layoutInflater) }

        override fun onCreate(savedInstanceState: Bundle?) {
            super.onCreate(savedInstanceState)
            setContentView(binding.root)

            binding.navigationView.setOnItemSelectedListener {item ->
                when(item.itemId) {
                    R.id.searchFragment -> setFragment(TAG_SEARCH, SearchFragment())
                    R.id.pinFragment -> setFragment(TAG_PIN, PinFragment())
                    R.id.homeFragment -> setFragment(TAG_HOME, HomeFragment())
                    R.id.myPageFragment -> setFragment(TAG_MY_PAGE, MyPageFragment())
                }
                true
            }
        }

        private fun setFragment(tag: String, fragment: Fragment) {
            val manager: FragmentManager = supportFragmentManager
            val fragTransaction = manager.beginTransaction()

            if(manager.findFragmentByTag(tag) == null) {
                fragTransaction.add(R.id.mainFrameLayout, fragment, tag)
            }
            val search = manager.findFragmentByTag(TAG_SEARCH)
            val pin = manager.findFragmentByTag(TAG_PIN)
            val home = manager.findFragmentByTag(TAG_HOME)
            val myPage = manager.findFragmentByTag(TAG_MY_PAGE)

            if(pin != null) {
                fragTransaction.hide(pin)
            }

            if(home != null) {
                fragTransaction.hide(home)
            }

            if(myPage != null) {
                fragTransaction.hide(myPage)
            }

            if(search != null) {
                fragTransaction.hide(search)
            }

            if(tag == TAG_PIN) {
                if(pin != null) {
                    fragTransaction.show(pin)
                }
            }

            if(tag == TAG_HOME) {
                if(home != null) {
                    fragTransaction.show(home)
                }
            }

            if(tag == TAG_MY_PAGE) {
                if(myPage != null) {
                    fragTransaction.show(myPage)
                }
            }

            if(tag == TAG_SEARCH) {
                if(search != null) {
                    fragTransaction.show(search)
                }
            }

            fragTransaction.commitAllowingStateLoss()
        }
    }

    // 캡쳐를 하면 화면이 짤리기 떄문에 쓴 코드를 그냥 복사함
    ```