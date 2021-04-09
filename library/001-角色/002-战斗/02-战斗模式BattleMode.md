# 战斗模式BattleMode
战斗状态下的状态机介绍


## BattleMode

![Image](amWiki/images/BattleMode1.png)
`图为AnimGraph中的 BattleMode部分`

可见基本的状态机为**BattleMove**

**BattleMove** 是基本的移动与跳跃功能

以腰部骨骼分层融合的 **插槽BlendAnim** 放入了[攻击Attack](?file=001-角色/002-战斗/03-攻击Attack "攻击Attack")的动画

**插槽DefaultSlot**中放入了[翻滚Dive](?file=001-角色/002-战斗/05-翻滚Dive "翻滚Dive")、[被击中和死亡BeenHitAndDead](?file=001-角色/002-战斗/06-被击中和死亡BeenHitAndDead "被击中和死亡BeenHitAndDead")的动画

### BattleMove

![Image](amWiki/images/BattleMode2.png)
`图为状态机BattleMode展开部分`

如图，跳跃部分和基础角色行动中的[跳跃Jump](?file=001-角色/001-基础角色行动/02-跳跃Jump "跳跃Jump")条件完全相同

### FightMove

![Image](amWiki/images/BattleMode3.png)
`图为状态机BattleMove展开部分`

如图，**FightMove** 是一个*2D混合空间播放器*，变量条件是在[基础行动BasicMove](?file=001-角色/001-基础角色行动/01-基础行动BasicMove "基础行动BasicMove")中提到过的 **`Speed`** **`Direction`**

![Image](amWiki/images/BattleMode4.png)
`图为FightMove的2D混合空间播放器`

图为打开后的FightMove的2D混合空间播放器

  -**``横轴``** 由 **`Speed`** 控制其是播放**跑步动画**还是**走动动画**

  -**``竖轴``** 由 **`Direction`** 控制不同的**方向动画**

## 角色蓝图中的走和慢跑

![Image](amWiki/images/BattleMode5.png)
`图为战斗模式中的加减速设置`

  -按住**Shift**时提速

  -松开**Shift**时减速
