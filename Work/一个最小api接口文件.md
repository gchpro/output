# 最小api接口文件

这是一个最小（最简洁）接口文件，包含了**必不可少**的 proc,doproc两个方法q


```python
#!usr/bin/python
#coding:utf-8

'''
	最小接口文件示例
'''

import g

def proc(conn, data):
    _res = doproc(conn,data)
    conn.response(_res)
    conn.send()

def doproc(conn, data):
    _res = {'s':1}
    _res['d'] = 'Hello World!'
    return _res
    
```

	#/usr/bin/python
	#coding:utf-8
	
	import g
	def 

当客户端发起请求的时候由serverweb进行接口分发，调用接口文件里的proc方法。conn为连接对象（类似socket连接对象）。

`data`为前端传过来的参数列表，例如大战国项目`api_fight_ready.py`战斗准备接口，`data=['pvguanka','1','1']`，`'pvguanka'` 为战斗类型，`'1'`为城池id，`'2'` 为关卡id。

返回值_res，一般为包含两个key，s和d，分表代表status状态位和data数据。

s为状态值，默认为1，表示调用成功；如果中间有条件判断未满足则会设置s为负值，并会有errmsg表示错误信息。例子如下：

```python
# 获取剩余可完成奏书任务次数
_num = g.m.zoushufun.getLessNum(uid)
# 如果剩余次数不足则报错
if _num < 1:
    _res['s'] = -1
    _res['errmsg'] = g.L('zoushu_refmatch_-1') # g.L() 是语言包模块
    return _res
```

如果接口执行成功，没有报错，则会把数据放在d里  **以前端需要的格式** 返回给前端。

```python
_gotarr = g.m.sfccfun.getSfccInfo(uid)
_res['d'] = {'gotarr':_gotarr}
return _res
```

```javascript
var yjssb = 'yanjun'
```

# This is header1

## This is header2

### This is header











清单

* aaa

* bb

* ccc

  ​

