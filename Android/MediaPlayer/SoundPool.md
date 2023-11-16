# Android --> MediaPlayer / SoundPool

*버튼을 클릭했을때 소리가 나오게 하려 위 두가지 방법을 사용해봄*

## SoundPool

* 효과음과 같이 짧은 것들을 재생할 때 사용한다.
* 버튼들을 연타해도 씹히거나 소리가 안나는등의 문제가 없다.
* 최대 볼륨은 1.0이다.

* 사용예제
    ![](https://cdn.discordapp.com/attachments/1154571973700112438/1174668604277530624/image.png?ex=65686e63&is=6555f963&hm=0bce25741bc94e08a4b0077d5febaeecbbc618cfeb26f716a262d70e03e6766c&)

<br>

## MediaPlayer

* 사용예제
    ```kt
    val mediaPlayer = MediaPlayer.create(this, R.raw.mi)

    button.setonClickListener {
        mediaPlayer.start()
    }

    // 사용이 끝나면 해제해주어야 한다
    mediaPlayer.release()
    ```