
## 基本信息

- 实体表示一类客观事物的总和，比如城市，歌手，歌曲名称，食物名称等
- 实体由一个实体名称，多个实体项，实体项的同义词组成  

## 实体命名规则

- 小写字母、数字、下划线组合
- 必须以字母开头
-  单词间下划线分割
- 缩写单词也用小写字母
- 长度2-50字符

## 实体项

实体中可能包含的单个单元，如城市的实体项，应该包括北京，上海，成都，深圳...  

## 同义词

- 每个实体项可以有多种不同的说法，如北京，当人们说：北京，北平，首都，帝都的时候，其实都是再说北京，所以要将北京，北平，首都，帝都这些同义词和北京联系起来，用来更好的理解用户意图。
- 不支持特殊字符（中点，下点）

## 系统共享实体

<table>
  <tr>
    <td>分类</td>
    <td >实体名称</td>
    <td width="200">实体描述</td>
    <td >举例</td>
    <td>返回数据格式</td>
  </tr>
  <tr>
    <td rowspan="2">时间</td>
    <td>sdate</td>
    <td>匹配日期</td>
    <td>明天，大后天明年三月四号，下个月五号国庆节等</td>
    <td>
      <div> {"year":"2017","month":"05",</div>
      <div>"day":"26","especial":"",</div>
      <div>"kind":0, "status":0,</div>
      <div>"leap":false,"delta":0,</div>
      <div>"yeardelta":0,"monthdelta":0}</div>
      <div>year :年(数字或者十二生肖)</div>
      <div>month:月(数字)</div>
      <div>day:日(数字</div>
      <div>especial：节日(24节气/重要节日)</div>
      <div>kind： 0:农历  1:公历</div>
      <div>status： 0:日期无误 1:日期有误</div>
      <div>leap: 当前输入的月份是否是闰月(如果说闰6月 则是ture)</div>
      <div>delta: 间隔的天数 例如: 三十之后的100天 delta:100</div>
      <div>yeardelta: 间隔的年数  例如:下个猴年三十儿yeardelta：12</div>
      <div>monthdelta: 间隔的月数 例如：三个月后的初一 monthdelta: 3</div>
    </td>
  </tr>
  <tr>
    <td>datatime</td>
    <td>
      匹配一个日期时间
      (有明确日期概念时。例如:
      三个小时之后，明天12点，
      12月23号上午7点45，
      给出日期+时间； 没有
      明确日期概念时。例如12点，
      下午两点，只给出时间。
      只支持公历日期)
    </td>
    <td>三个小时之后,下午两点</td>
    <td>{"date":"2017-01-01", "time":"08:00:00", "meridian":"am", "illegal":0}</td>
  </tr>
  <tr>
    <td rowspan="2">数字</td>
    <td>number</td>
    <td>数字</td>
    <td>一万零三十</td>
    <td>10030</td>
  </tr>
  <tr>
    <td>ordinal</td>
    <td>序数</td>
    <td>第8个</td>
    <td>8</td>
  </tr>
  <tr>
    <td rowspan="6">计量</td>
    <td>unit_area</td>
    <td>匹配面积(基准单位m2)</td>
    <td>1平方米</td>
    <td>{"amount":1,"unit":"m2"}</td></tr>
  <tr>
    <td>unit_currency</td>
    <td>
       <div>匹配汇率(unit是</div>
       <div>变化的 范围参考</div>
       <div>(https://en.wi</div>
       <div>kipedia.org/wiki</div>
       <div>/ISO_4217))</div>
    </td>
    <td>10美</td>
    <td>{"amount":10,"unit":"USD"}</td>
  </tr>
  <tr>
    <td>unit_lenght</td>
    <td>匹配长度(基准单位m)</td>
    <td>5厘米</td>
    <td>{"amount":0.05,"unit":"m"}</td>
  </tr>
  <tr>
    <td>unit_speed</td>
    <td>匹配速度(基准单位km/h)</td>
    <td>6千米每小时</td>
    <td>{"amount":6,"unit":"km/h"}</td>
  </tr>
  <tr>
    <td>unit_volume</td>
    <td>匹配体积(基准单位l)</td>
    <td>890毫升</td>
    <td>{"amount":0.89,"unit":"l"}</td>
  </tr>
  <tr>
    <td>unit_weight</td>
    <td>匹配重量(基准单位g)</td>
    <td>9斤</td>
    <td>{"amount":4500,"unit":"g"}</td>
  </tr>
  <tr>
    <td rowspan="4">地理信息</td>
    <td>geo_country</td>
    <td>国家</td>
    <td>不丹</td>
    <td>不丹</td>
  </tr>
  <tr>
    <td>geo_province</td>
    <td>中国省份</td>
    <td>河南省</td>
    <td>河南省</td>
  </tr>
  <tr>
    <td>geo_city</td>
    <td>中国地级城市及以上城市</td>
    <td>北京市</td>
    <td>北京市</td>
  </tr>
  <tr>
    <td>geo_district</td>
    <td>中国区/县</td>
    <td>朝阳区</td>
    <td>朝阳区</td>
  </tr>
  <tr>
    <td rowspan="2">通用匹配</td>
    <td>any</td>
    <td>任何字符，包括空 都在该实体中。这个实体相当于正则中的*。和default的区别见any/default实体区别</td>
    <td>打电话给@sys.any:name打电话给李XX</td>
    <td>李XX</td>
  </tr>
  <tr>
    <td>default</td>
    <td>任何字符，包括空 都在该实体中。这个实体相当于正则中的*。和any的区别见any/default实体区别</td>
    <td>例如：英译汉场景。进入场景后，只要没有退出场景，所有后面的输入都需要翻译。就需要在场景中配置一个只有default的模板来匹配所有的输入，来实现这个功能。</td>
    <td></td>
  </tr>
</table>

### any/default实体区别

|-|any|default|
|---|---|---|
| 优先级|跨场景模板比较中，处于低优先级。|跨场景模板比较中，处于高优先级。|
|使用场景|如果需要一个通配的实体，并且使用这个实体的场景是一个可以随时跳到别的场景，那么使用@sys.any|如果需要一个通配实体，并且这个模板所在的场景是一个相对来说比较封闭的场景，可能这个通配实体要获取所有的东西都送到该场景中进行处理(如翻译场景，认为进入场景之后，所有的query都是需要翻译的话)，那么使用@sys.default|
