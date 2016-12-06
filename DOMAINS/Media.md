## 2.9 Media

---

### 2.1.1 服务说明

> \(**Media**\)

### 2.1.2 意图说明

> 该服务主要有37个意图\(**Action**\)，相应的功能、名称介绍如下。
>
>
> 1 . **Play**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Play |   |   | media,need_confirm | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | date | @sys.date |   |
>   | name | @sys.entity.media_buildin |   |
>   | peri | @sys.entity.time_period |   |
>   | repeat | @sys.entity.media_repeat |   |
>   | time | @sys.time |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"我要听刘德华的忘情水",
    "semantic":{
        "action":"Play",
        "params":{
            "name":{
                "code":0,
                "norm":"忘情水",
                "orgin":"忘情水"
            },
            "artist":{
                "code":0,
                "norm":"刘德华",
                "orgin":"刘德华"
            }
        },
        "service":"Media"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "album":"我的少女时代 电影原声带",
            "resId":"music:4146218",
            "name":"忘情水",
            "extra":{
                "style":"",
                "httpheaders":{
                    "Cookie":"pgv_pvid=6710; qqmusic_uin=38418; qqmusic_key=6854504056; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481023549399",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 2 . **Play**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Play |   |   | media,need_confirm | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | date | @sys.date |   |
>   | keyword | @sys.entity.media_childsong_content |   |
>   | peri | @sys.entity.time_period |   |
>   | repeat | @sys.entity.media_repeat |   |
>   | time | @sys.time |   |
>   | type | @sys.entity.media_type |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"我要听刘德华的忘情水",
    "semantic":{
        "action":"Play",
        "params":{
            "name":{
                "code":0,
                "norm":"忘情水",
                "orgin":"忘情水"
            },
            "artist":{
                "code":0,
                "norm":"刘德华",
                "orgin":"刘德华"
            }
        },
        "service":"Media"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "album":"我的少女时代 电影原声带",
            "resId":"music:4146218",
            "name":"忘情水",
            "extra":{
                "style":"",
                "httpheaders":{
                    "Cookie":"pgv_pvid=5956; qqmusic_uin=76520; qqmusic_key=8741185635; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481023549829",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 3 . **Play**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Play |   |   | media,need_confirm | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | date | @sys.date |   |
>   | keyword | @sys.entity.media_story_content |   |
>   | peri | @sys.entity.time_period |   |
>   | repeat | @sys.entity.media_repeat |   |
>   | time | @sys.time |   |
>   | type | @sys.entity.media_type |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"我要听刘德华的忘情水",
    "semantic":{
        "action":"Play",
        "params":{
            "name":{
                "code":0,
                "norm":"忘情水",
                "orgin":"忘情水"
            },
            "artist":{
                "code":0,
                "norm":"刘德华",
                "orgin":"刘德华"
            }
        },
        "service":"Media"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "album":"我的少女时代 电影原声带",
            "resId":"music:4146218",
            "name":"忘情水",
            "extra":{
                "style":"",
                "httpheaders":{
                    "Cookie":"pgv_pvid=1626; qqmusic_uin=91484; qqmusic_key=7032853035; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481023550244",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 4 . **Play**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Play |   |   | media,need_confirm | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | artist | @sys.entity.media_singer |   |
>   | date | @sys.date |   |
>   | fuz_artist | @sys.any |   |
>   | fuz_name | @sys.any |   |
>   | keyword | @sys.entity.media_music_keyword |   |
>   | name | @sys.entity.media_song_strong |   |
>   | peri | @sys.entity.time_period |   |
>   | repeat | @sys.entity.media_repeat |   |
>   | time | @sys.time |   |
>   | type | @sys.entity.media_type |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"我要听刘德华的忘情水",
    "semantic":{
        "action":"Play",
        "params":{
            "name":{
                "code":0,
                "norm":"忘情水",
                "orgin":"忘情水"
            },
            "artist":{
                "code":0,
                "norm":"刘德华",
                "orgin":"刘德华"
            }
        },
        "service":"Media"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "album":"我的少女时代 电影原声带",
            "resId":"music:4146218",
            "name":"忘情水",
            "extra":{
                "style":"",
                "httpheaders":{
                    "Cookie":"pgv_pvid=7431; qqmusic_uin=16360; qqmusic_key=3127323152; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481023550691",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 5 . **Play**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Play |   |   | media,need_confirm | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | date | @sys.date |   |
>   | keyword | @sys.entity.media_childsong_keyword |   |
>   | name | @sys.entity.media_childsong |   |
>   | peri | @sys.entity.time_period |   |
>   | repeat | @sys.entity.media_repeat |   |
>   | time | @sys.time |   |
>   | type | @sys.entity.media_type |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"我要听刘德华的忘情水",
    "semantic":{
        "action":"Play",
        "params":{
            "name":{
                "code":0,
                "norm":"忘情水",
                "orgin":"忘情水"
            },
            "artist":{
                "code":0,
                "norm":"刘德华",
                "orgin":"刘德华"
            }
        },
        "service":"Media"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "album":"我的少女时代 电影原声带",
            "resId":"music:4146218",
            "name":"忘情水",
            "extra":{
                "style":"",
                "httpheaders":{
                    "Cookie":"pgv_pvid=7038; qqmusic_uin=72126; qqmusic_key=5537112644; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481023551065",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 6 . **Play**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Play |   |   | media,need_confirm | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | date | @sys.date |   |
>   | keyword | @sys.entity.media_story_keyword |   |
>   | name | @sys.entity.media_story |   |
>   | peri | @sys.entity.time_period |   |
>   | repeat | @sys.entity.media_repeat |   |
>   | time | @sys.time |   |
>   | type | @sys.entity.media_type |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"我要听刘德华的忘情水",
    "semantic":{
        "action":"Play",
        "params":{
            "name":{
                "code":0,
                "norm":"忘情水",
                "orgin":"忘情水"
            },
            "artist":{
                "code":0,
                "norm":"刘德华",
                "orgin":"刘德华"
            }
        },
        "service":"Media"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "album":"我的少女时代 电影原声带",
            "resId":"music:4146218",
            "name":"忘情水",
            "extra":{
                "style":"",
                "httpheaders":{
                    "Cookie":"pgv_pvid=209; qqmusic_uin=15804; qqmusic_key=5672373893; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481023551449",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 7 . **Play**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Play |   |   | media,need_confirm | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | artist | @sys.entity.media_sketch_artist |   |
>   | date | @sys.date |   |
>   | fuz_name | @sys.any |   |
>   | name | @sys.entity.media_sketch |   |
>   | peri | @sys.entity.time_period |   |
>   | repeat | @sys.entity.media_repeat |   |
>   | time | @sys.time |   |
>   | type | @sys.entity.media_type |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"我要听刘德华的忘情水",
    "semantic":{
        "action":"Play",
        "params":{
            "name":{
                "code":0,
                "norm":"忘情水",
                "orgin":"忘情水"
            },
            "artist":{
                "code":0,
                "norm":"刘德华",
                "orgin":"刘德华"
            }
        },
        "service":"Media"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "album":"我的少女时代 电影原声带",
            "resId":"music:4146218",
            "name":"忘情水",
            "extra":{
                "style":"",
                "httpheaders":{
                    "Cookie":"pgv_pvid=8212; qqmusic_uin=15673; qqmusic_key=8362227874; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481023551849",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 8 . **Play**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Play |   |   | media,need_confirm | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | artist | @sys.entity.media_crosstalk_artist |   |
>   | date | @sys.date |   |
>   | fuz_name | @sys.any |   |
>   | name | @sys.entity.media_crosstalk |   |
>   | peri | @sys.entity.time_period |   |
>   | repeat | @sys.entity.media_repeat |   |
>   | time | @sys.time |   |
>   | type | @sys.entity.media_type |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"我要听刘德华的忘情水",
    "semantic":{
        "action":"Play",
        "params":{
            "name":{
                "code":0,
                "norm":"忘情水",
                "orgin":"忘情水"
            },
            "artist":{
                "code":0,
                "norm":"刘德华",
                "orgin":"刘德华"
            }
        },
        "service":"Media"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "album":"我的少女时代 电影原声带",
            "resId":"music:4146218",
            "name":"忘情水",
            "extra":{
                "style":"",
                "httpheaders":{
                    "Cookie":"pgv_pvid=6429; qqmusic_uin=93603; qqmusic_key=4405706456; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481023552190",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 9 . **Play**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Play |   |   | media,need_confirm | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | date | @sys.date |   |
>   | name | @sys.entity.media_joke |   |
>   | peri | @sys.entity.time_period |   |
>   | repeat | @sys.entity.media_repeat |   |
>   | time | @sys.time |   |
>   | type | @sys.entity.media_type |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"我要听刘德华的忘情水",
    "semantic":{
        "action":"Play",
        "params":{
            "name":{
                "code":0,
                "norm":"忘情水",
                "orgin":"忘情水"
            },
            "artist":{
                "code":0,
                "norm":"刘德华",
                "orgin":"刘德华"
            }
        },
        "service":"Media"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "album":"我的少女时代 电影原声带",
            "resId":"music:4146218",
            "name":"忘情水",
            "extra":{
                "style":"",
                "httpheaders":{
                    "Cookie":"pgv_pvid=5150; qqmusic_uin=25685; qqmusic_key=6004906832; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481023552634",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 10 . **Play**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Play |   |   | media,need_confirm | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | date | @sys.date |   |
>   | name | @sys.entity.media_storytelling |   |
>   | peri | @sys.entity.time_period |   |
>   | repeat | @sys.entity.media_repeat |   |
>   | type | @sys.entity.media_type |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"我要听刘德华的忘情水",
    "semantic":{
        "action":"Play",
        "params":{
            "name":{
                "code":0,
                "norm":"忘情水",
                "orgin":"忘情水"
            },
            "artist":{
                "code":0,
                "norm":"刘德华",
                "orgin":"刘德华"
            }
        },
        "service":"Media"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "album":"我的少女时代 电影原声带",
            "resId":"music:4146218",
            "name":"忘情水",
            "extra":{
                "style":"",
                "httpheaders":{
                    "Cookie":"pgv_pvid=2821; qqmusic_uin=13245; qqmusic_key=1000293932; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481023553091",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 11 . **Play**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Play |   |   | media,need_confirm | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | date | @sys.date |   |
>   | name | @sys.entity.media_yuOpera |   |
>   | peri | @sys.entity.time_period |   |
>   | repeat | @sys.entity.media_repeat |   |
>   | time | @sys.time |   |
>   | type | @sys.entity.media_type |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"我要听刘德华的忘情水",
    "semantic":{
        "action":"Play",
        "params":{
            "name":{
                "code":0,
                "norm":"忘情水",
                "orgin":"忘情水"
            },
            "artist":{
                "code":0,
                "norm":"刘德华",
                "orgin":"刘德华"
            }
        },
        "service":"Media"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "album":"我的少女时代 电影原声带",
            "resId":"music:4146218",
            "name":"忘情水",
            "extra":{
                "style":"",
                "httpheaders":{
                    "Cookie":"pgv_pvid=1642; qqmusic_uin=15643; qqmusic_key=6992692965; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481023553535",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 12 . **Play**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Play |   |   | media,need_confirm | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | date | @sys.date |   |
>   | name | @sys.entity.media_huangmeixi |   |
>   | peri | @sys.entity.time_period |   |
>   | repeat | @sys.entity.media_repeat |   |
>   | time | @sys.time |   |
>   | type | @sys.entity.media_type |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"我要听刘德华的忘情水",
    "semantic":{
        "action":"Play",
        "params":{
            "name":{
                "code":0,
                "norm":"忘情水",
                "orgin":"忘情水"
            },
            "artist":{
                "code":0,
                "norm":"刘德华",
                "orgin":"刘德华"
            }
        },
        "service":"Media"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "album":"我的少女时代 电影原声带",
            "resId":"music:4146218",
            "name":"忘情水",
            "extra":{
                "style":"",
                "httpheaders":{
                    "Cookie":"pgv_pvid=8206; qqmusic_uin=36539; qqmusic_key=3814297939; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481023553983",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 13 . **Play**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Play |   |   | media,need_confirm | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | date | @sys.date |   |
>   | name | @sys.entity.media_two_person_act |   |
>   | peri | @sys.entity.time_period |   |
>   | repeat | @sys.entity.media_repeat |   |
>   | time | @sys.time |   |
>   | type | @sys.entity.media_type |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"我要听刘德华的忘情水",
    "semantic":{
        "action":"Play",
        "params":{
            "name":{
                "code":0,
                "norm":"忘情水",
                "orgin":"忘情水"
            },
            "artist":{
                "code":0,
                "norm":"刘德华",
                "orgin":"刘德华"
            }
        },
        "service":"Media"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "album":"我的少女时代 电影原声带",
            "resId":"music:4146218",
            "name":"忘情水",
            "extra":{
                "style":"",
                "httpheaders":{
                    "Cookie":"pgv_pvid=9881; qqmusic_uin=41082; qqmusic_key=8450908745; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481023554443",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 14 . **Play**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Play |   |   | media,need_confirm | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | date | @sys.date |   |
>   | name | @sys.entity.media_whys |   |
>   | peri | @sys.entity.time_period |   |
>   | repeat | @sys.entity.media_repeat |   |
>   | time | @sys.time |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"我要听刘德华的忘情水",
    "semantic":{
        "action":"Play",
        "params":{
            "name":{
                "code":0,
                "norm":"忘情水",
                "orgin":"忘情水"
            },
            "artist":{
                "code":0,
                "norm":"刘德华",
                "orgin":"刘德华"
            }
        },
        "service":"Media"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "album":"我的少女时代 电影原声带",
            "resId":"music:4146218",
            "name":"忘情水",
            "extra":{
                "style":"",
                "httpheaders":{
                    "Cookie":"pgv_pvid=7779; qqmusic_uin=99743; qqmusic_key=8165899599; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481023554855",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 15 . **Play**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Play |   |   | media,need_confirm | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | date | @sys.date |   |
>   | name | @sys.entity.media_yueopera |   |
>   | peri | @sys.entity.time_period |   |
>   | repeat | @sys.entity.media_repeat |   |
>   | time | @sys.time |   |
>   | type | @sys.entity.media_type |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"我要听刘德华的忘情水",
    "semantic":{
        "action":"Play",
        "params":{
            "name":{
                "code":0,
                "norm":"忘情水",
                "orgin":"忘情水"
            },
            "artist":{
                "code":0,
                "norm":"刘德华",
                "orgin":"刘德华"
            }
        },
        "service":"Media"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "album":"我的少女时代 电影原声带",
            "resId":"music:4146218",
            "name":"忘情水",
            "extra":{
                "style":"",
                "httpheaders":{
                    "Cookie":"pgv_pvid=7206; qqmusic_uin=10018; qqmusic_key=3288548339; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481023555291",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 16 . **Play**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Play |   |   | media,need_confirm | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | artist | @sys.entity.poetry_author |   |
>   | date | @sys.date |   |
>   | name | @sys.entity.media_poetry_title |   |
>   | peri | @sys.entity.time_period |   |
>   | reader | @sys.entity.media_poetry_reader |   |
>   | repeat | @sys.entity.media_repeat |   |
>   | time | @sys.time |   |
>   | type | @sys.entity.media_type |   |
>   | verse | @sys.entity.poetry_content |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"我要听刘德华的忘情水",
    "semantic":{
        "action":"Play",
        "params":{
            "name":{
                "code":0,
                "norm":"忘情水",
                "orgin":"忘情水"
            },
            "artist":{
                "code":0,
                "norm":"刘德华",
                "orgin":"刘德华"
            }
        },
        "service":"Media"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "album":"我的少女时代 电影原声带",
            "resId":"music:4146218",
            "name":"忘情水",
            "extra":{
                "style":"",
                "httpheaders":{
                    "Cookie":"pgv_pvid=8740; qqmusic_uin=35180; qqmusic_key=3167336732; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481023555725",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 17 . **Play**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Play |   |   | media,need_confirm | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | date | @sys.date |   |
>   | keyword | @sys.entity.media_music_keyword_strong |   |
>   | name | @sys.entity.media_song_strong |   |
>   | peri | @sys.entity.time_period |   |
>   | repeat | @sys.entity.media_repeat |   |
>   | time | @sys.time |   |
>   | type | @sys.entity.media_type |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"我要听刘德华的忘情水",
    "semantic":{
        "action":"Play",
        "params":{
            "name":{
                "code":0,
                "norm":"忘情水",
                "orgin":"忘情水"
            },
            "artist":{
                "code":0,
                "norm":"刘德华",
                "orgin":"刘德华"
            }
        },
        "service":"Media"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "album":"我的少女时代 电影原声带",
            "resId":"music:4146218",
            "name":"忘情水",
            "extra":{
                "style":"",
                "httpheaders":{
                    "Cookie":"pgv_pvid=6022; qqmusic_uin=35377; qqmusic_key=7883171836; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481023556146",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 18 . **Play**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Play |   |   | media,need_confirm | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | artist | @sys.entity.media_singer |   |
>   | fuz_name | @sys.any |   |
>   | keyword | @sys.entity.media_music_keyword |   |
>   | name | @sys.entity.media_song_strong |   |
>   | repeat | @sys.entity.media_repeat |   |
>   | singer | @sys.entity.media_singer |   |
>   | type | @sys.entity.media_type |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"我要听刘德华的忘情水",
    "semantic":{
        "action":"Play",
        "params":{
            "name":{
                "code":0,
                "norm":"忘情水",
                "orgin":"忘情水"
            },
            "artist":{
                "code":0,
                "norm":"刘德华",
                "orgin":"刘德华"
            }
        },
        "service":"Media"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "album":"我的少女时代 电影原声带",
            "resId":"music:4146218",
            "name":"忘情水",
            "extra":{
                "style":"",
                "httpheaders":{
                    "Cookie":"pgv_pvid=6526; qqmusic_uin=37480; qqmusic_key=1348588336; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481023556558",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 19 . **Play**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Play |   |   | media,need_confirm | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | artist | @sys.entity.media_singer |   |
>   | keyword | @sys.entity.media_music_keyword |   |
>   | name | @sys.entity.media_song |   |
>   | repeat | @sys.entity.media_repeat |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"我要听刘德华的忘情水",
    "semantic":{
        "action":"Play",
        "params":{
            "name":{
                "code":0,
                "norm":"忘情水",
                "orgin":"忘情水"
            },
            "artist":{
                "code":0,
                "norm":"刘德华",
                "orgin":"刘德华"
            }
        },
        "service":"Media"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "album":"我的少女时代 电影原声带",
            "resId":"music:4146218",
            "name":"忘情水",
            "extra":{
                "style":"",
                "httpheaders":{
                    "Cookie":"pgv_pvid=2167; qqmusic_uin=54480; qqmusic_key=7501667829; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481023556993",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
