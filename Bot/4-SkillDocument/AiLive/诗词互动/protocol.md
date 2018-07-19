
## 意图
按照诗词互动功能，分为以下7个意图：

意图  | 例句  |  备注
--|---|--
Learn  |  我要学静夜思<br>我要学诗词 |
Read  | 我要读静夜思<br>我要读李白的诗  |
Abut(对)  | 我要对答静夜思  |
Recite  | 我要背诵静夜思  |
Next  | 下一关  |
Prev  |  上一关 |
Repeat  | 重复学习  |

## response

返回结果如下json所示。
语音输出方案在response的result字段里的outputSpeech中，以数组的形式，依次读出。目前支持PlainText格式和ssml格式。

query: 我要学静夜思

response:

```
{
  "results": [
    {
      "hint": "小朋友，跟我一起来学吧，静夜思，唐朝，李白，床前明月光，疑是地上霜，举头望明月，低头思故乡，知识需要重复记忆才能掌握哦，是重复学习、还是进入下一关呢？",
      "outputSpeech": {
        "items": [
          {
            "type": "PlainText",
            "source": "小朋友，跟我一起来学吧"
          },
          {
            "type": "SSML",
            "source": "<p>静夜思</p>\n<p><s>唐朝</s><s>李白</s></p>\n<s>床前<breaktime=\"100ms\"/><emphasis>明</emphasis>月光</s>\n<s>疑是<breaktime=\"100ms\"/><emphasis>地</emphasis>上霜</s>\n<s>举头<breaktime=\"100ms\"/><emphasis>望</emphasis>明月</s>\n<s>低头<breaktime=\"100ms\"/><emphasis>思</emphasis>故乡</s>"
          },
          {
            "type": "PlainText",
            "source": "知识需要重复记忆才能掌握哦，是重复学习、还是进入下一关呢？"
          }
        ]
      },
      "outputDisplay": {},
      "data": {
        "author": [
          "李白"
        ],
        "title": "静夜思",
        "dynasty": [
          "唐朝"
        ],
        "content": [
          "床前明月光",
          "疑是地上霜",
          "举头望明月",
          "低头思故乡"
        ],
        "length": 20
      }
    }
  ]
}
```
