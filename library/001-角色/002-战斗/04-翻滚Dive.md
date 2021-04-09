# 翻滚Dive
`不知道Dive有没有翻滚的意思但是我看它是翻滚的动画所以做成翻滚了`

### 翻滚蒙太奇

![Image](amWiki/images/Dive2.png)
``图为翻滚的蒙太奇文件``

这段蒙太奇由三部分组成

 -翻前动作Dive_Fwd_Start（无rootmotion)

 -翻时动作Dive_Fwd_Loop（有rootmotion)

 -起身动作Dive_Fwd_Roll（无rootmotion）

``三段动画本身的速度不太理想多少有加速，只有一段有rootmotion的话为了流畅只能调整速度来感觉``

### 蓝图部分

![Image](amWiki/images/Dive.png)
`图为翻滚的蓝图部分`

如图，因为只有前翻滚的动画所以只用了双击W的写法，射击时设置了布尔变量，用于防止多次翻滚的 **`Dive Able`**,防止被自己的攻击打断动画的 **`Attack Able`** 无敌时间 **`Can Be Hurt`**,并播放蒙太奇动画*Dive_Montage* 和*CameraShake*
