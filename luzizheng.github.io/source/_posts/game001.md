---
title: 饥荒联机版控制台代码大全
date: 2021-11-26 11:57:09
tags: 遊戲 
categories: 第九藝術探索
cover: https://cdn.jsdelivr.net/gh/luzizheng/images@master/img/dont-starve-together-commands.jpeg
banner: https://cdn.jsdelivr.net/gh/luzizheng/images@master/img/dont-starve-together-commands.jpeg
---

![img](https://cdn.jsdelivr.net/gh/luzizheng/images@master/img/dont-starve-together-commands.jpeg)

## 玩家命令
> #动作预测，必须在控制台的本地模式下执行该命令才有效。
`ThePlayer:EnableMovementPrediction(true)`

> #你可以合成任何东西。
`ThePlayer.components.builder:GiveAllRecipes()`

> #生命值上限
`ThePlayer.components.health:SetMaxHealth(value)`

> #理智值上限，改变你的角色 的生命 值上限。
`ThePlayer.components.sanity:SetMax(value)`

> #饥饿值上限，改变你的角色 的饥饿 值上限。
`ThePlayer.components.hunger:SetMax(value)`

> #暂停饥饿，你的角色 不再降低饥饿值。
`ThePlayer.components.hunger:Pause(true)`

> #伤害倍数，改变你的角色 的伤害倍数。
`ThePlayer.components.combat.damagemultiplier = value`

> #海狸，把伍迪 变成海狸 。把 .01 改为 1 可以让你变回伍迪。
`ThePlayer.components.beaverness:SetPercent(.01)`

## 其他玩家命令

> #列出所有玩家的用户名和编号
`c_listallplayers()`

> #取一个玩家
`AllPlayers[number] `

> #对所有玩家使用同一命令,只修改command，用其他命令代替command，使用 "v" 代替命令中的 AllPlayers[number]。例如， "for k,v in pairs(AllPlayers) do c_move(v) end" 将会把所有玩家都移动到鼠标所指的位置。
`for k,v in pairs(AllPlayers) do command end `

> #移动一个玩家,移动玩家到鼠标所指的位置。
`c_move(AllPlayers[number])`

> #杀死一个玩家
`AllPlayers[number]:PushEvent('death')`

> #复活玩家
`AllPlayers[number]:PushEvent('respawnfromghost')`

> #传送至玩家,传送到对应编号的玩家，玩家编号可以通过 c_listallplayers() 获取。
`c_goto(AllPlayers[number]) `

> #丢掉玩家物品栏的物品
`AllPlayers[number].components.inventory:DropEverything() `

> #让玩家重新选择角色,使用该命令将会删除玩家物品栏的物品而不会掉落，所以推荐你先让玩家的物品丢掉他们的物品，或者使用上一条命令 DropEverthing()。
`c_despawn(AllPlayers[number]) `

> #截至2016年6月25日，增加了一个新的命令来指定玩家。你可以通过一个玩家名UserToPlayer('玩家名') 来指定一个玩家而不是使用玩家编号。例如，杀死一名叫做 "PlayerA" 的玩家，他的用户编号为5，你可以执行：
`AllPlayers[5]:PushEvent('death') `

> #但在此之前你必须先运行 c_listallplayers() 来知道玩家编号，十分麻烦。为了简单一点地执行命令，你可以把命令改成：
`UserToPlayer('PlayerA'):PushEvent('death')`

## 世界命令

> dowhat
`whatcode`