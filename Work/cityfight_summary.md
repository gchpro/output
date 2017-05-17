# 城战总结

## 最小城战代码片段

```python
#!/usr/bin/python
#coding:utf-8

import g
from fightcity import FIGHTCITY,Army

# 准备数据
# 队伍信息 
addData = {
  'uid':uid,
  'isuser':1,
  'attk':1,
  'head':gud['head'],
  'name':gud['name'],
  'lv':gud['lv'],
  'side':side,
  'heros':fightData,
  'bztype':bztype,
  'status':2,
  'killnum':0
}

cityid = '1'
fid = g.C.getUniqCode()
initData = {'npcnum':10, 'maxnpc':10}

# 实例化城战
cfight = FIGHTCITY(cityid, fid, 'pvcity', initData)
cfight.xztime = xzTime
teamid = cfight.getUnqid()
addData['armyid'] = teamid

# 实例化队伍信息
joinArmy = Army(addData)

# 将队伍信息添加到等待的队伍
cfight.addWaitArmy(joinArmy)

# 战斗逻辑开始
cfight.fightStart()

# 通知客户端
cfight.sendFightId()
```

## 工作流

1. 实例化城战类，初始化所需数据。cfight = FIGHTCITY(cityid, fid, 'pvcity', initData)
2. 初始化队伍信息，joinArmy = Army(addData)
3. 将队伍加入到等待队列中， cfight.addWaitArmy(joinArmy)
4. 开始战斗， cfight.fightStart() -> line.step() -> fres = self.fight.doFightRes(_army0, _army1)




## 流程

初始化战斗 －> 开始战斗 －> 已投入的部队开打－>如果有新加入的部队则加入等待队列

我方打赢了npc －》npc －》 检测是否打完 —— 打完则结束，否则新生成npc。



