### Templates
* [Concept](#Concept)
* [Sample](#Sample)

### Concept{#Concept}
 
---

Templates，模板。一套规则，当这个规则被满足时，模板对应的意图（Intent）就会被激发。同时，满足规则时规则中相应的Parameters也会被填充，传递给意图。

### Sample{#Sample}

---
同样的例子：
问：今天天气怎么样？
答：今天有点冷。

Template：@sys.date:date天气怎么样
问题：今天天气怎么样，满足了该模板，并且参数date被填充了：今天
那么该Template对应的Intent对应的动作就会被激发，同时带着参数“今天”