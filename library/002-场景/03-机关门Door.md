# 机关门Door
![Image](amWiki/images/Door1.png)

`图为两种机关门`

## Door1
![Image](amWiki/images/Door2.png)
![Image](amWiki/images/Door5.png)
`图为Door1蓝图`

>Door1由两个BoxCollision、两个文本渲染组件和一个静态网格体（Door）组成

其中一个BoxCollision只任关卡中的一个球体
当这个球和BoxCollision触发重叠后就会通过相对平移移开静态网格体达到开门的效果，并且关闭第一个文本渲染组件，开启第二个文本渲染组件的可视性

另一个用于玩家通过时重叠后关闭另一个文本组件

## Door2
![Image](amWiki/images/Door3.png)
![Image](amWiki/images/Door4.png)
![Image](amWiki/images/Door6.png)
`图为Door2蓝图`

>Door2由三块静态网格体和三个相对的BoxCollision组成

所有BoxCollision都只在于玩家射出的子弹A才会触发后续节点，实现开关门，布尔节点是为了防止多次触发
