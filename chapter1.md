# 导航接口

1. # 服务背景

  提供导航和周边搜索等语义功能。
2. # 槽位

  1. | Slot\_Key | Description | Main\_Application | Example |
    | --- | --- | --- | --- |
    | locations | 地点列表 | 用于导航，搜索等。
    返回结果时会将其拆分成location，
    name，street，building number | 清华大学南门
    海淀区
    肯德基
    北苑路和春华路交叉口
    美立方9栋 |
    | location\_reference | 方位词 | 用户导航，搜索等 | 前方
    目的地 |
    | price\_modifier | 价格修饰词 | 用户导航，搜索等 | 便宜的
    性价比高的 |
    | quality\_modifier | 质量修饰词 | 用户导航，搜索等 | 好的
    很赞的 |
    | traffic\_category | 交通类型 | 用户导航，搜索等 | 路口
    交叉口 |



