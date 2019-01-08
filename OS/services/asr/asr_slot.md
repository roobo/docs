# slot

slot(槽)是一种特殊的规则，它描述了一系列记号的并列关系，且不包含任何子规则。

离线指令词支持slot的概念，可以动态的设置slot，动态的修改离线识别的内容。

## 典型场景
打电话场景
为了达到较为精确匹配，需要将联系人加入到离线识别中，而联系人并不是固定的，所以当联系人改变时，需要动态的修改联系人信息，这时就可以用到slot

## 使用方法

1. 声明slot

    如果是在bnf中声明slot，请参照[语法规则中的示例](./asr_offline_grammar.md##示例)

    如果是动态加载带slot的grammar，请参照[离线命令词中的示例](./asr_offline.md####示例)

2. 更新slot内容

    通过AsrManager接口可以对slot进行更新
    ```java

    /**
     * 用来动态加载slot集合，将bnf中定义的slot填充为具体内容, 覆盖原来slot的内容
     *
     * @param grammarName 　grammar 名字
     * @param slotwordMap 　具体slot的内容，　key为slot的名字，value为slot的内容
     * @param listener    　设置结果回调
     */
    public void setSlotWordList(
            final String grammarName,
            final String moduleName,
            final Map<String, Map<String, List<String>>> slotwordMap,
            final LoadGrammarListener listener);

    /**
     * 动态移除slot的内容
     *
     * @param grammarName 　grammar 名字
     * @param moduleID    　默认为场景名
     * @param context     　默认为场景名
     * @param listener    　移除结果回调
     */
    public void removeSlotWordList(
            final String grammarName,
            final String moduleID,
            final String context,
            final LoadGrammarListener listener);


    Map<String, Map<String, List<String>>> slotWordMap = new HashMap<>();
    final List<String> contactSlotContent = new ArrayList<>();
    contactSlotContent.add("张三");
    contactSlotContent.add("李四");
    slotWordMap.put("module_name", new HashMap<String, List<String>>() {{put("contact", contactSlotContent);}});
    AsrManager.getInstance().setSlotWordList("grammar_name", "module_name", slotWordMap, new LoadGrammarListener() {
        @Override
        public void onResult(boolean success, String grammarName) {

        }
    });

    ```