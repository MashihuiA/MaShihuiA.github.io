# *基础行动BasicMove*

键鼠对角色的控制和一些重要的布尔值

## 角色蓝图中的基本的移动和保存变量
### 键鼠对角色的控制
![Image](amWiki/images/基础行动1.png)

由输入轴**Turn**区分左右得到变量 **`Mouse X`**

由输入轴**LookUp**区分左右得到变量 **`Mouse Y`**

>由**获得控制旋转**创建旋转体获得**向前**和**向右**的向量作为键盘输入时**添加移动输入**

### 保存变量
![Image](amWiki/images/基础行动2.png )

为了之后会常用**镜头晃动**而提前提升为变量，可直接从左边拖出使用 **`CameraController`**

生成角色生命值 **`HealthPoint(HP)`**

## 角色动画蓝图中的基础保存变量

![Image](amWiki/images/BasicMove3.png)

由Pawn的拥有者**获取其速度**获得**向量长度**提升为变量 **`Speed`**

由Pawn的拥有者**获取Actor旋转**与**获取速度**用节点**计算方向**提升为变量 **`Direction`**

在角色蓝图中的**CharacterMovement**中有自带的计算角色是否在空中，将其提升为变量 **`In Air`**


## AnimGraph

![Image](amWiki/images/BasicMove4.png)

`图为AnimGraph中的基础行动BasicMove的状态机`

![Image](amWiki/images/Jump2.png)

`图为基础行动BasicMove状态机的展开`

><font color=#1aa0ff>【**Idle**待机动画】</font>

进入状态机时无任何操作的基本动画

><font color=#1aa0ff>【**Spring_Fwd_Start**起跑动作】</font>

当 **`Speed`>0时** 时从*Idle待机*转换为*Spring_Fwd_Start起跑*

><font color=#1aa0ff>【**Spring_Fwd**奔跑循环动画】</font>

当 **`Spring_Fwd_Start播放动画时间剩余部分`<=0.6** 时从*Spring_Fwd_Start起跑*转换为*Spring_Fwd奔跑循环*

`因为原FBX文件动画时间过长此时动画剩余部分比较多的时候就要转换对于操作比较自然`

><font color=#1aa0ff>【**Spring_Fwd_Stop**惯性停止动画】</font>

当 **`Speed`=0** 时从*Spring_Fwd奔跑循环*转换为*Spring_Fwd_Stop惯性停止*

当**Spring_Fwd_Stop相关动画剩余部分<=0.33**时从*Spring_Fwd_Stop惯性停止*转换为*Idle待机*

`取0.33的值是为了前后脚的顺序而调整的数值`

`*Spring_Fwd_Stop*并不是RootMotion动画但是为了不在播放期间出现滑步还是启用了根骨骼动画，但是还是无法避免它本身无动画位移的现实而在原地移动`

>**只在起跑的时候设置了CameraShake，让起步的动感更强于运动中，很多行为动作中都带有不同的CameraShake**
