# 存档点CheckPoint

## 游戏模式蓝图中的设置

![Image](amWiki/images/CheckPoint1.png)

创建重生**Respawn**的自定义事件，设置一次重生点变量 **`Respawn Position`** ,并绑定事件到销毁事件，每次销毁时都会创建重生UI,选择重生后会通过蓝图通信在 **`Respawn Position`** 生成角色，并再触发一次 **`Respawn Position`** ,绑定事件到销毁事件

## CheckPoint蓝图中的设置

![Image](amWiki/images/CheckPoint2.png)

当角色于CheckPoint重叠时将组件中的公告板组件的变换位置并设置给游戏模式蓝图中的 **`Respawn Position`**
