# 战斗场地BattleField

![Image](amWiki/images/BattleField.png)
`图为战斗场地的蓝图`

>组成部分只有一个*Box Collision*

  -若是玩家和Box Collision重叠则通过蓝图通信允许战斗
  -若是玩家离开Box Collision则取消战斗允许

蓝图通讯到的目标蓝图在[战斗切换BattleChange](?file=001-角色/002-战斗/01-战斗切换BattleChange "战斗切换BattleChange")解释
