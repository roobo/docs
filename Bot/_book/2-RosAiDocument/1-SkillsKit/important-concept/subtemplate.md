# 基本信息

子模板表示能抽象出来的一类小模板
# 语法

## []语法
- []中用|来进行字，词的分割，表示“或”
- []中可以有固定的字词或者实体

## []语法示例
- [A|B|CD]EF 表示AEF或BEF或CDEF
- [A|@sys.date:date|] 表示A或@sys.date或空

# 示例
拿机票做例，出发地可以进行抽象，命名为startCity，
子模板内容为：[从@sys.entity.city:city起飞|@sys.entity:city:city起飞|从@sys.entity:city:city]（注意不能使用<<>>语法）。  <br>
引用子模板时，将其置于<<>>中（且只能放置在这个语法中），使用@pattern.startCity来引用,如<<@pattern.startCity>>
如果需要引用系统子模板，需要用@sys.pattern.XXX
