# 跳跃Jump
跳跃不管是基础行动还是战斗模式都能触发

## 跳跃动画所需的变量

### 角色蓝图中

![Image](amWiki/images/Jump1.png)

由项目设置中自带的 **输入操作Jump** 触发 **跳跃事件** 并播放起跳蒙太奇 **Jump_Start_Montage**

为了不产生空中再次触发跳跃动画设置了布尔变量`Jumpable`

 -在按下时设置为 **false**

 -在落地动画中的通知时再次设置为 **Ture**

### 角色动画蓝图中
![Image](amWiki/images/Jump4.png)
`图为跳跃检测①`
![Image](amWiki/images/Jump5.png)
`图为跳跃检测②`
![Image](amWiki/images/Jump6.png)
`图为跳跃检测③`
![Image](amWiki/images/Jump7.png)
`图为跳跃检测④`

*图片条约检测④* 中

在 *Jump_Fall_Loop跳跃空中循环动画* 时添加了**曲线通知**，用于判断角色是否应该产生**检测球体**

*图片条约检测①* 中

通过*Actor位置*的向量作为*检测球体*的**开头Start**

通过角色蓝图的一个向下的*箭头组件*来*获取向前向量*，由此向量乘以一个很大的数值并与*Actor位置*相加获得的向量作为*检测球体*的**结尾End**

*检测球体时* 中

取得Distance提升为高度变量 **`High`**

#### 落地检测

当**`High`小于等于100**时，设置布尔值 **`AboutLand`** 为Ture

#### 高点检测

*图片条约检测 ③* 中

当并未到落地动画前也就是**`High`并不小于等于100**时，会到一个Do once的节点中，第一次会计算 **`High`-`LastHigh`** ,若是刚开始下降的时候那一定是这一瞬间计算的高度低于上一次计算的高度，也就是当  **`High`-`LastHigh`<0** 时判断为最高点
 **`AboutApex`** 为**Ture**,并不会再次触发

若是判断为否就将 **`High`** 的值设置为 **`LastHigh`**，这也是第一次获得的 **`LastHigh`** 的值，并重制Do once


## AnimGraph
![Image](amWiki/images/Jump2.png)
`图为AnimGraph中基础行动状态机`

><font color=#1aa0ff>【**Jump_Start_Montage** 起跳动画】</font>

在角色蓝图中按下 **输入操作Jump** 时触发，并未写入状态机



><font color=#1aa0ff>【**Jump_Fall_Loop** 空中循环动画】</font>

当布尔值 **`In Air`为Ture** 时由*Idle待机*转换为*Jump_Fall_Loop跳跃空中循环*

`虽然状态机中是*Idle*到*Jump_Fall_Loop*但其实在此之前有触发*Jump_Start_Montage*作为真正的过渡动画`



><font color=#1aa0ff>【**Jump_Apex** 跳跃最高点动画】</font>

当**`AboutApex`为Ture**时从*Jump_Fall_Loop跳跃空中循环*转换为*Jump_Apex跳跃最高点*

当**Jump_Apex的相关剩余动画时间<=0.2**时从*Jump_Apex跳跃最高点*再转换回*Jump_Fall_Loop跳跃空中循环*



><font color=#1aa0ff>【**Jump_Land** 落地前空中动画】</font>

当**`AboutLand`为Ture**时从*Jump_Fall_Loop跳跃空中循环*转换到*Jump_Land落地前空中动画*



><font color=#1aa0ff>【**Jump_Recovery** 接触地面时落地动画】</font>

过渡规划的*细节面板*中的**基于状态中序列播放**打勾后会在*Jump_Land落地前空中动画*播放完动画后转换为*Jump_Recovery接触地面时落地动画*

当**Jump_Recovery接触地面时落地动画的相关剩余动画时间<=0.2**时从*Jump_Recovery接触地面时落地动画*转换为*Idle待机*

`为了播放Jump_Recovery接触地面时落地动画不产生滑步而设置为了根骨骼动画，但是因为动画播放时间略长且动作幅度大不能把速度调整过快导致这个动作时间过长，略微影响操作流畅性`

![Image](amWiki/images/Jump3.png)
`在战斗模式下同样有跳跃的逻辑，原理完全相同`
