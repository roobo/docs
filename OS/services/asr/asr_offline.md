# 离线指令词

离线指令词分为两种
- 免唤醒离线指令词
- 唤醒状态下的离线指令词

## 免唤醒离线指令词

免唤醒离线指令词可以通过两种方式定义：静态声明和动态加载

### 静态声明

1. 根据[语法规则](./asr_offline_grammar.md)编写离线识别语法文件(*.bnf)
2. 将写好的语法文件放到场景assets目录
3. 在AndroidManifest.xml的application标签中声明
   - ASR_FILE_PATH 表示bnf语法文件的路径，路径是相对语assets目录的
   - ASR_GRAMMAR_NAME 代表该语法文件的唯一名字

```xml
<meta-data
    android:name="ASR_FILE_PATH"
    android:value="grammar_file_name.bnf"/>

<meta-data
    android:name="ASR_GRAMMAR_NAME"
    android:value="grammar_name"/>
```

### 动态加载

#### 动态加载免唤醒离线指令词可以通过AsrManager提供的接口

```java
/**
* 通过bnf文件加载离线指令词.
* 
* @param grammarName         grammar 名称
* @param grammarPathInAssets grammar文件(bnf+)在assets下的路径
* @param moduleID            场景名
* @param listener            加载结果回调
* @param grammarType         指定生效范围, 详见 AsrGrammarType
*/
public void loadGrammarFromAssets(final String grammarName,
                                    final String grammarPathInAssets,
                                    final String moduleID,
                                    final LoadGrammarListener listener,
                                    final int grammarType);

/**
* 动态创建Grammar文件加载离线指令词
*
* @param asrGrammar 详解查看AsrGrammar
* @param moduleID   场景名
* @param listener   加载结果回调
*/
public void loadGrammar(AsrGrammar asrGrammar, String moduleID, LoadGrammarListener listener);
```

#### 示例

```java
    
AsrManager.getInstance().loadGrammarFromAssets("grammar_name", "grammar_file_name.bnf", "module_name", new LoadGrammarListener() {
                @Override
                public void onResult(boolean success, String grammarName) {
                }
            }, AsrGrammarType.TYPE_GLOBAL_OFFLINE);

Map<String, String> startTagMap = new HashMap<>();
startTagMap.put("music_open", "[帮我]打开音乐");
startTagMap.put("music_close", "(关闭|退出)音乐");
startTagMap.put("call", "打电话给<contact>");
AsrGrammar asrGrammar = new AsrGrammar.Builder("grammar_name", AsrGrammarType.TYPE_GLOBAL_OFFLINE, startTagMap).build();
AsrManager.getInstance().loadGrammar(asrGrammar, "module_name", new LoadGrammarListener() {
    @Override
    public void onResult(boolean success, String grammarName) {

    }
});

```

## 唤醒状态下的离线指令词

唤醒状态下的离线指令词只可以动态加载，动态加载的方式同**免唤醒离线指令词**的动态加载方式一样，只是需要将AsrGrammarType.TYPE_GLOBAL_OFFLINE修改为AsrGrammarType.TYPE_WAKED_OFFLINE