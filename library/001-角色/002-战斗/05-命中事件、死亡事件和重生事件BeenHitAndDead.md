# 命中事件、死亡事件和重生事件

## 受击事件

![Image](amWiki/images/Death1.png)
![Image](amWiki/images/Death2.png)

如图，收到[攻击Attack](?file=001-角色/002-战斗/03-攻击Attack "攻击Attack")后根据不同的方向传输过来播放不同的受击动画
  -前方受到攻击HitReact_Front_Montage
  -后方受到攻击HitReact_Back_Montage
  -左方受到攻击HitReact_Left_Montage
  -右方受到攻击HitReact_Right_Montage

每次收到攻击都会设置 **`HealthPoint`** -10

>若是攻击有不同的武器效果伤害这个数值应该写在武器或者子弹蓝图里

## 死亡事件

当 **`HealthPoint`=0** 时布尔通过进行死亡动画，设置为只能看UI，角色设置为布娃娃

  -若最后一击被击中的是背部则是播放背部受击的死亡动画Death_Bwd
  -若最后一击被击中的是前/左/右方向死亡皆为前方受击的死亡动画Death_Fwd

>因为大部分玩家被射中第一下都会转身和敌人战斗，猜侧大部分玩家还是会死于正面的攻击

## 死亡事件

销毁有绑定到游戏模式蓝图中到[存档点CheckPoint](?file=002-场景/02-存档点CheckPoint "存档点CheckPoint")
