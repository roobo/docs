### NluHelper
NluHelper提供了使用本地NLU的方法。  
为了使用本地NLU，开发者需要按照下面的步骤操作：
* 创建包含实体，子模版，模糊匹配项和意图的xml文件。
* 在代码中将xml文件添加到本地NLU中
* 根据业务运行数据，添加或者更新实体，子模版，模糊匹配项
* 在场景退出的时候移除xml文件。此时所有文件中声明的实体，子模版，模糊匹配项以及意图都会被移除。

#### 接口说明
```java
// 增加新的语法文件
public static boolean addGrammar(Context context, String module, String grammarFile);

//增加新的语法文件
public static boolean addGrammar(Context context, String module, RMLObject grammarRml);

//移除已有的语法文件
public static boolean removeGrammar(Context context, String module, String grammarFile);

//移除已有的语法文件
public static boolean removeGrammar(Context context, String module, RMLObject grammarRml);

//获取定义好的实体
public static Map<String, List<String>> getEntity(Context context, String module, String entityName);

//更新实体
public static boolean updateEntity(Context context, String module, String entityName, Map<String, List<String>> entities);

//增加新的实体
public static boolean addEntity(Context context, String module, String entityName, final String entityItemName, final List<String> entityAlias);

//增加新的实体
public static boolean addEntity(Context context, String module, String entityName, Map<String, List<String>> entityItems);

//移除实体
public static boolean removeEntity(Context context, String module, String entityName, final String entityItemName, final List<String> entityAlias);

//移除实体
public static boolean removeEntity(Context context, String module, String entityName, Map<String, List<String>> entityItems);

//增加新的模糊匹配
public static void addFuzzyMatch(Context context, String module, String fuzzyName, Map<String, Set<String>> fuzzyItems);

//移除已有的模糊匹配
public static void removeFuzzyMatch(Context context, String module, String fuzzyName, Map<String, Set<String>> fuzzyItems);

//更新已有的模糊匹配
public static void updateFuzzyMatch(Context context, String module, String fuzzyName, Map<String, ? extends Set<String>> fuzzyItems);

//获取定义好的模糊匹配项
public static Map<String,Set<String>> getFuzzyMatchItems(Context context, String module, String fuzzyItemName);
```
NluHelper主要提供针对模板文件，实体和模糊匹配项的操作。  

子模版和意图定义在模板文件中，可以通过xml文本以及RML两种方式添加到离线NLU中。增加和移除模板文件时，需要指定当前的模块名称。由一个模块名称增加的模板文件，只能由这个模块移除。

针对实体的操作，包括获取，更新，增加和移除。除了模块名称之外，还需要指定实体名和规约项的内容。一类实体包括了多个从文本列表到规约项的映射。

针对模糊匹配的操作，包括获取，更新，增加和移除。与实体类似。