# 战斗切换BattleChange
考虑到很多游戏其实不希望玩家在大街上拔枪只是希望角色在战斗场所战斗所以最好有个战斗模式并且有特定的 *战斗场地BattleField*

## 战斗场地BattleField
[战斗场地BattleField](?file=002-场景/01-战斗场地BattleField "战斗场地BattleField")

## 角色蓝图中的过程

![Image](amWiki/images/BattleChange1.png)
`图为战斗切换①`
![Image](amWiki/images/BattleChange2.png)
`图为战斗切换②`
![Image](amWiki/images/BattleChange3.png)
`图为战斗切换③`

*图片战斗切换①* 中

  -进入[战斗场地BattleField](?file=002-场景/01-战斗场地BattleField "战斗场地BattleField")后就会触发蓝图接口事件**In To The Fight**，设置 **`Can Fight`** 为**Ture**

  -离开[战斗场地BattleField](?file=002-场景/01-战斗场地BattleField "战斗场地BattleField")后会强制取消战斗，设置 **`Can Fight`** 和 **`Fight`** 为**False**并设置 **`Max Walk Speed`** 为**600**

*图片战斗切换 ② ③* 中

当**输入操作BattleChange**（Tab)时通过节点Flip Flop触发事件

  -第一次设置 **`Fight`** 为 **Ture**，
  **`Max Walk Speed`** 减速设置为 **200** 播放蒙太奇动画 **Respawn_Montage** 的同时随着时间轴扩大 **视野**

>有趣的是Respawn这个动画本是作为重生的动画，但是因为设定为只有在战斗场地才能战斗那让角色一出来就抬枪再放下手感觉很奇怪，而且这个动作作为拔枪动作还挺合适的于是就用到了切换为战斗的过渡动作


  -第二次设置 **`Fight`** 为 **False**，
  **`Max Walk Speed`** 还原速度设置为 **600** 并随着时间轴缩小 **视野**

>**`Use Controller Rotation Yaw`** 和 **`Orient Rotation to Movement`** 的设置是为了切换操纵视角，在战斗模式中设置为角色随着镜头旋转一直背对镜头，而普通模式下镜头并不约束角色的方向

## AnimGraph
![Image](amWiki/images/BattleChange4.png)
`图为AnimGraph`

如图可见，状态机[战斗切换BattleChange](?file=001-角色/002-战斗/01-战斗切换BattleChange "战斗切换BattleChange")的上面大框就是[战斗模式BattleMode](?file=001-角色/002-战斗/02-战斗模式BattleMode "战斗模式BattleMode")

两者的切换方式靠布尔变量 **`FightA`** 来切换

>将角色蓝图中的 **`Fight`** 在动画蓝图中使用提升变量不能重名，于是设置为了 **`FightA`** （A代表Anim)
