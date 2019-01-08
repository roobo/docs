# 离线指令词语法规则

离线指令词语法文件遵循BNF(Backus-Naur Form)语法规则

## 示例

```bnf

#BNF+EMV2.1;
!grammar demo;
!start <bar>;
!start <pay>;
!start <call>;

!slot <contact>;

<drink> : 纯净水|[百事]柠檬汁|啤酒|白酒;

<order> : [请|麻烦]给我一杯<drink>;

<question> : 你这里有<drink>吗;

<bar> : <order>|<question>;

<pay> : 结账;

<call> : 打电话给<contact>;

```

## 语法说明

|语法|说明|
|:--|:--|
|;|定义结束符，所有定义结束后都需要添加该符号|
|!|自留字开始声明。可用的自留字：grammar，start，slot等|
|<rule_name>|规则。定义了一系列记号及其相互的关系，且可以包含其它子规则。通过指定规则的唯一名称，使其它的规则可以通过该名称引用该规则|
|<rule_name>:sentences|规则内容|

## 文件组成部分

* 文件自标识头

    #BNF+EMV2.1;

* 语法名称

    !grammar grammar_name;

    注意：需要保证grammar_name是唯一的

* 初始规则声明

    !start() <规则名称>;

* 槽声明 槽是一种特殊的规则，它描述了一系列记号的并列关系，且不包含任何子规则

    !slot <slot_name>;

* 规则内容

    <rule_name> : sentences;

    sentences由句子组成，多个句子可以通过|分隔
    * 句子中[]表示可选项，[]中可以使用|表示或的关系
    * 句子中()表示必选项，()中可以使用|表示或的关系
    * 句子中可以通过<>引用别的规则或者槽

### 

