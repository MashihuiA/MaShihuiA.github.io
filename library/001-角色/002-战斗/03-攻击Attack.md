# 攻击Attack

## 射击动作

![Image](amWiki/images/Attack1.png)
``图为角色蓝图中的两种射击触发节点``

### 慢速射击

**左键**按下后，有默认打开的*Gate节点*，通过后播放*DoubleShot_Fire_Lft_Montage动画*和*CameraShake*,通过序列依次进行三条线

  -生成子弹

  -**关闭** Gate的通过权

  -在自己设定的 **`SlowShot CD`** 延迟后**开启**通过权达到慢速半自动射击的效果

### 快速射击

**右键** 按下时设置 **`Attack Able`** 为**Ture**,播放*DoubleShot_Fire_Lft_Fast_Montage动画*和*CameraShake*，通过序列一次进行两条线

  -生成子弹

  -在自己设定的 **`FastShot CD`** 延迟后无限循环快速射击动作

**右键** 送开时将 **`Attack Able`** 设置为 **False**，取消连续射击

## 子弹生成

### 生成子弹位置的设置

![Image](amWiki/images/Attack3.png)
`图为生成子弹的骨骼插槽位置`
![Image](amWiki/images/Attack2.png)
`图为生成子弹的蓝图部分`

如图，子弹从*WeaponA*和*WeaponB*两个插槽位置位置生成子弹并在飞行途中飞行到生成子弹时镜头朝向的位置

### 子弹

![Image](amWiki/images/Attack4.png)
`图为两种子弹`

>ProjectileA

主角生成，对[机关门Door](?file=002-场景/03-机关门Door "机关门Door")2号有开关认定，对自己也会有效果

>ProjectileB

[子弹陷阱Trap](?file=002-场景/04-子弹陷阱Trap "子弹陷阱Trap")生成，对角色有攻击效果，蓝图与A子弹完全相同

### 子弹蓝图

![Image](amWiki/images/Attack8.png)

子弹包含UE4自带的投掷组件，速度调快就是子弹

![Image](amWiki/images/Attack5.png)
`图为两种子弹销毁事件`

  -生成2s后自行销毁

  -命中基元自建后添加冲量后自行销毁

![Image](amWiki/images/Attack6.png)
`图为子弹命中判断方向的蓝图部分①`
![Image](amWiki/images/Attack7.png)
`图为子弹命中判断方向的蓝图部分②`

如图,子弹在击中角色之后立刻提升为变量 **`Target`** 并以 **`Target`** 和 **`Self`** 的位置通过向量DOT得出两个数值变量 **`FB`**
和 **`LR`** 来判断击中时的**前后**和**左右**并最后分别通过四种不同的蓝图接口事件传递给**`Target`**
