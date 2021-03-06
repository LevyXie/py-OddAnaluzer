# Python足彩欧赔分析器

## 一、原理

本小程序的设计理念，来自一个老铁的玄学思路：根据当前足彩比赛的即时赔率，历史同赔比赛赔率及历史同赔比赛赛果，分析对比，预测当前比赛赛果。

具体实现如下：

- 爬取500彩票网的同赔数据，采用立博、威廉希尔及Bet365的即时欧赔数据源，获取历史同赔比赛。
- 根据爬取所有历史同赔比赛，进行数据分析
  - 针对每场比赛的历史赔率与当前即时赔率，分别计算两者胜平负三项的方差和，获取方差最小的场次，作为**推荐参照场次**。
  - 针对每场比赛的历史赔率与当前即时赔率，若两者胜平负中最近似数据差值<0.05，且其他两者数据差值<0.2，列为**相似赔率场次**。

- 输出推荐参照场次及相似赔率场次，供用户参考。

## 二、主要工具及包

- PyQt5 + QtDesigner + PyUic + PyRcc：设计图形化界面
- qt_material：美化图形化界面
- request + BeatifulSoup：爬取数据

## 二、使用步骤

- 进入500彩票网足彩界面：https://live.500.com/

- 点击任意比赛的欧赔链接，进入百家欧赔页面，复制其url（或者直接在这里右键复制链接）。

![image-20220520233938396](https://myimageserver.oss-cn-beijing.aliyuncs.com/img/image-20220520233938396.png)

- 向UI界面url选项输入复制的url，并选择参照的数据源。如下：

<img src="https://myimageserver.oss-cn-beijing.aliyuncs.com/img/image-20220520234144081.png" alt="image-20220520234144081" style="zoom:67%;" />

- 点击一键生成比赛策略，结果如下：

<img src="https://myimageserver.oss-cn-beijing.aliyuncs.com/img/image-20220520234229591.png" alt="image-20220520234229591" style="zoom:67%;" />

- 其中今日推荐策略及历史同赔赛果可供参考，详见原理部分。

## 三、备注

- 本项目仅用于个人练习Python使用。
- 本项目中的爬虫尚未使用代理IP等措施，过于频繁爬取数据可能会被反爬虫机制禁用IP；同时过于频繁爬取数据会对网站服务器造成一定压力，不建议频繁爬取哦。
- 由于对Python语法还不是很熟悉，很多地方的代码比较冗余，后期有待优化。

ps：经实战分析，似乎并不好用，记录一下，图一乐。︿(￣︶￣)︿

