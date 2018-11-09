# 基本信息 
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
## 实体实体
<table >
<tr><td width="100px">分类</td><td width="140px">实体名称</td><td width="140px">实体描述</td><td width="200px">举例</td><td width="200px">返回数据格式</td></tr>

<tr><td rowspan="2">时间</td><td>sdate</td><td>匹配日期</td><td>明天，大后天明年三月四号，下个月五号国庆节等</td>
<td>
{"year":"2017","month":"05","day":"26","especial":"","kind":0,"status":0,"leap":false,"delta":0,"yeardelta":0,"monthdelta":0}
type SDate struct {
    Year string `json:"year"` // 十二生肖，所以是string
    Month string `json:"month"` // 与year保持一致
    Day string `json:"day"` // 与year保持一致
    Especial string `json:"especial"` // 三十儿,二十四节气啥的，每年不确定是哪一天的
    Kind LunisolarCalendar `json:"kind"` // 农历，公历
    Status SysFuncStatusCode `json:"status"` // 状态
    LeapMonth bool `json:"leap"` // 是否是闰月
    Delta int `json:"delta"` //天数，做推理用（三十之后的100天，只支持天数）。 因为农历每个月的日子不固定，service自己算
    YearDelta int `json:"yeardelta"` // 例：下一个猴年，yeardelta：12， 上一个猴年: yeardelta: -12
    MonthDelta int `json:"monthdelta"` //例：三个月后的初一，因为是阴历，所以这个月是几月框架没有概念。
}
</td></tr>

<tr><td>datatime</td><td>匹配一个日期时间</td><td>三个小时之后,下午两点</td>
<td>有明确日期概念时（三个小时之后，明天12点，12月23号上午7点45 等），给出日期+时间； 没有明确日期概念时（12点，下午两点），只给出时间。 只支持公历日期
</td></tr>

<tr><td rowspan="2">数字</td><td>number</td><td>数字</td><td>一万零三十</td><td>10030</td></tr>
<tr><td>ordinal</td><td>序数</td><td>第8个</td><td>8</td></tr>
<tr><td rowspan="6">计量</td><td>unit_area</td><td>匹配面积(基准单位m2)</td><td>1平方米</td><td>{"amount":1,"unit":"m2"}</td></tr>
<tr><td>unit_currency</td><td>匹配汇率(unit 是变化的 范围参考 [ISO 4217}(https://en.wikipedia.org/wiki/ISO_4217))</td><td>10美元</td><td>{"amount":10,"unit":"USD"}
</td></tr>
<tr><td>unit_lenght</td><td>匹配长度(基准单位m)</td><td>5厘米</td><td>{"amount":0.05,"unit":"m"}</td></tr>
<tr><td>unit_speed</td><td>匹配速度(基准单位km/h)</td><td>6千米每小时</td><td>{"amount":6,"unit":"km/h"}</td></tr>
<tr><td>unit_volume</td><td>匹配体积(基准单位l)</td><td>890毫升</td><td>{"amount":0.89,"unit":"l"}</td></tr>
<tr><td>unit_weight</td><td>匹配重量(基准单位g)</td><td>9斤</td><td>{"amount":4500,"unit":"g"}</td></tr>

<tr><td rowspan="4">地理信息</td><td>geog_country</td><td>国家</td><td>不丹</td><td>不丹</td></tr>
<tr><td>geog_province</td><td>中国省份</td><td>河南省</td><td>河南省</td></tr>
<tr><td>geog_city</td><td>中国地级城市及以上城市</td><td>北京市</td><td>北京市</td></tr>
<tr><td>geog_district</td><td>中国区/县</td><td>朝阳区</td><td>朝阳区</td></tr>

<tr><td rowspan="2">通用匹配</td><td>any</td><td>匹配任何字符或者空。同一模板中优先级最低，先匹配其他槽位。</td><td>模板：
打电话给@sys.any:name
打电话给李XXX</td><td></td></tr>
<tr><td>default</td><td>在模板中单独使用，需要配置上文,匹配任何字符。</td><td>例如：英译汉场景。进入场景后，只要没有退出场景，所有后面的输入都需要翻译。就需要在场景中配置一个只有default的模板来匹配所有的输入，来实现这个功能。</td><td></td></tr>
</table>
	


