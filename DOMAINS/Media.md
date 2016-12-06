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
                    "Cookie":"pgv_pvid=606; qqmusic_uin=34859; qqmusic_key=1080348144; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481020577445",
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
                    "Cookie":"pgv_pvid=4325; qqmusic_uin=81263; qqmusic_key=9501753184; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481020577920",
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
                    "Cookie":"pgv_pvid=8203; qqmusic_uin=74231; qqmusic_key=4526210078; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481020578344",
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
                    "Cookie":"pgv_pvid=449; qqmusic_uin=56537; qqmusic_key=7479323393; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481020578754",
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
                    "Cookie":"pgv_pvid=349; qqmusic_uin=12257; qqmusic_key=5247751686; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481020579201",
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
                    "Cookie":"pgv_pvid=2806; qqmusic_uin=84108; qqmusic_key=5351758712; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481020579682",
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
                    "Cookie":"pgv_pvid=9605; qqmusic_uin=18757; qqmusic_key=8946633856; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481020580109",
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
                    "Cookie":"pgv_pvid=2659; qqmusic_uin=50384; qqmusic_key=1349898260; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481020580503",
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
                    "Cookie":"pgv_pvid=6862; qqmusic_uin=69687; qqmusic_key=4922047420; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481020580980",
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
                    "Cookie":"pgv_pvid=7660; qqmusic_uin=30387; qqmusic_key=4204324594; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481020581405",
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
                    "Cookie":"pgv_pvid=8449; qqmusic_uin=92668; qqmusic_key=1347986457; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481020581843",
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
                    "Cookie":"pgv_pvid=1633; qqmusic_uin=53268; qqmusic_key=6672734699; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481020582286",
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
                    "Cookie":"pgv_pvid=5745; qqmusic_uin=10387; qqmusic_key=7344199344; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481020582722",
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
                    "Cookie":"pgv_pvid=7424; qqmusic_uin=94903; qqmusic_key=5380261872; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481020583140",
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
                    "Cookie":"pgv_pvid=143; qqmusic_uin=59035; qqmusic_key=2382992372; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481020583593",
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
                    "Cookie":"pgv_pvid=426; qqmusic_uin=98412; qqmusic_key=6878875332; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481020584023",
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
                    "Cookie":"pgv_pvid=4444; qqmusic_uin=20332; qqmusic_key=8944262096; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481020584447",
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
                    "Cookie":"pgv_pvid=5420; qqmusic_uin=24447; qqmusic_key=1015089709; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481020584850",
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
                    "Cookie":"pgv_pvid=23; qqmusic_uin=92474; qqmusic_key=2287149580; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481020585284",
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
