## Media

* [服务说明](#服务说明)
* [意图说明](#意图说明)
 * [Play](#1Play)
 * [Play](#2Play)
 * [Play](#3Play)
 * [Play](#4Play)
 * [Play](#5Play)
 * [Play](#6Play)
 * [Play](#7Play)
 * [Play](#8Play)
 * [Play](#9Play)
 * [Play](#10Play)
 * [Play](#11Play)
 * [Play](#12Play)
 * [Play](#13Play)
 * [Play](#14Play)
 * [Play](#15Play)
 * [Play](#16Play)
 * [Play](#17Play)
 * [Play](#18Play)
 * [Prev](#19Prev)
 * [Next](#20Next)
 * [Pause](#21Pause)
 * [Resume](#22Resume)
 * [Exit](#23Exit)
 * [Resume](#24Resume)
 * [Resume](#25Resume)
 * [Resume](#26Resume)
 * [Resume](#27Resume)
 * [Resume](#28Resume)
 * [Resume](#29Resume)
 * [Resume](#30Resume)
 * [Resume](#31Resume)
 * [Resume](#32Resume)
 * [Resume](#33Resume)
 * [Resume](#34Resume)
 * [Resume](#35Resume)
 * [Play](#36Play)

### 服务说明 {#服务说明}

---

\(**Media**\)

### 意图说明 {#意图说明}

---

该服务主要有36个意图\(**Action**\)，相应的功能、名称介绍如下。

| 名称 | 功能 | 上文 | 下文 |
| :---: | :---: | :---: | :---: |
| Play |  |  | media,need_confirm |
| Play |  |  | media,need_confirm |
| Play |  |  | media,need_confirm |
| Play |  |  | media,need_confirm |
| Play |  |  | media,need_confirm |
| Play |  |  | media,need_confirm |
| Play |  |  | media,need_confirm |
| Play |  |  | media,need_confirm |
| Play |  |  | media,need_confirm |
| Play |  |  | media,need_confirm |
| Play |  |  | media,need_confirm |
| Play |  |  | media,need_confirm |
| Play |  |  | media,need_confirm |
| Play |  |  | media,need_confirm |
| Play |  |  | media,need_confirm |
| Play |  |  | media,need_confirm |
| Play |  |  | media,need_confirm |
| Play |  |  | media,need_confirm |
| Prev |  | media | media |
| Next |  | media | media |
| Pause |  | media | media |
| Resume |  | media | media |
| Exit |  | media | media |
| Resume |  | media | media |
| Resume |  | media | media |
| Resume |  | media | media |
| Resume |  | media | media |
| Resume |  | media | media |
| Resume |  | media | media |
| Resume |  | media | media |
| Resume |  | media | media |
| Resume |  | media | media |
| Resume |  | media | media |
| Resume |  | media | media |
| Resume |  | media | media |
| Play |  | need_confirm | media |

#### Play {#1Play}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| date | @sys.date |  |
| name | @sys.entity.media_buildin |  |
| peri | @sys.entity.time_period |  |
| repeat | @sys.entity.media_repeat |  |
| time | @sys.time |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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
                    "Cookie":"pgv_pvid=5138; qqmusic_uin=97269; qqmusic_key=5840766390; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481198004621",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}

```

#### Play {#2Play}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| date | @sys.date |  |
| keyword | @sys.entity.media_childsong_content |  |
| peri | @sys.entity.time_period |  |
| repeat | @sys.entity.media_repeat |  |
| time | @sys.time |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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
                    "Cookie":"pgv_pvid=3255; qqmusic_uin=10381; qqmusic_key=7729041084; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481198005051",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}

```

#### Play {#3Play}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| date | @sys.date |  |
| keyword | @sys.entity.media_story_content |  |
| peri | @sys.entity.time_period |  |
| repeat | @sys.entity.media_repeat |  |
| time | @sys.time |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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
                    "Cookie":"pgv_pvid=4079; qqmusic_uin=44653; qqmusic_key=3507761656; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481198005555",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}

```

#### Play {#4Play}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| artist | @sys.entity.media_singer |  |
| date | @sys.date |  |
| fuz_artist | @sys.any |  |
| fuz_name | @sys.any |  |
| keyword | @sys.entity.media_music_keyword |  |
| name | @sys.entity.media_song_strong |  |
| peri | @sys.entity.time_period |  |
| repeat | @sys.entity.media_repeat |  |
| time | @sys.time |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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
                    "Cookie":"pgv_pvid=5687; qqmusic_uin=80398; qqmusic_key=4729426847; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481198006031",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}

```

#### Play {#5Play}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| date | @sys.date |  |
| keyword | @sys.entity.media_childsong_keyword |  |
| name | @sys.entity.media_childsong |  |
| peri | @sys.entity.time_period |  |
| repeat | @sys.entity.media_repeat |  |
| time | @sys.time |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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
                    "Cookie":"pgv_pvid=8834; qqmusic_uin=98279; qqmusic_key=9981871577; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481198006556",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}

```

#### Play {#6Play}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| date | @sys.date |  |
| keyword | @sys.entity.media_story_keyword |  |
| name | @sys.entity.media_story |  |
| peri | @sys.entity.time_period |  |
| repeat | @sys.entity.media_repeat |  |
| time | @sys.time |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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
                    "Cookie":"pgv_pvid=493; qqmusic_uin=38457; qqmusic_key=2309274464; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481198007050",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}

```

#### Play {#7Play}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| artist | @sys.entity.media_sketch_artist |  |
| date | @sys.date |  |
| fuz_name | @sys.any |  |
| name | @sys.entity.media_sketch |  |
| peri | @sys.entity.time_period |  |
| repeat | @sys.entity.media_repeat |  |
| time | @sys.time |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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
                    "Cookie":"pgv_pvid=6207; qqmusic_uin=70527; qqmusic_key=9806900220; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481198007554",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}

```

#### Play {#8Play}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| artist | @sys.entity.media_crosstalk_artist |  |
| date | @sys.date |  |
| fuz_name | @sys.any |  |
| name | @sys.entity.media_crosstalk |  |
| peri | @sys.entity.time_period |  |
| repeat | @sys.entity.media_repeat |  |
| time | @sys.time |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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
                    "Cookie":"pgv_pvid=812; qqmusic_uin=85420; qqmusic_key=6104578423; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481198008005",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}

```

#### Play {#9Play}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| date | @sys.date |  |
| name | @sys.entity.media_joke |  |
| peri | @sys.entity.time_period |  |
| repeat | @sys.entity.media_repeat |  |
| time | @sys.time |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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
                    "Cookie":"pgv_pvid=7639; qqmusic_uin=28791; qqmusic_key=9512572176; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481198008416",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}

```

#### Play {#10Play}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| date | @sys.date |  |
| name | @sys.entity.media_storytelling |  |
| peri | @sys.entity.time_period |  |
| repeat | @sys.entity.media_repeat |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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
                    "Cookie":"pgv_pvid=4619; qqmusic_uin=86304; qqmusic_key=7256995339; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481198008858",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}

```

#### Play {#11Play}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| date | @sys.date |  |
| name | @sys.entity.media_yuOpera |  |
| peri | @sys.entity.time_period |  |
| repeat | @sys.entity.media_repeat |  |
| time | @sys.time |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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
                    "Cookie":"pgv_pvid=1314; qqmusic_uin=72830; qqmusic_key=6161650400; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481198009333",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}

```

#### Play {#12Play}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| date | @sys.date |  |
| name | @sys.entity.media_huangmeixi |  |
| peri | @sys.entity.time_period |  |
| repeat | @sys.entity.media_repeat |  |
| time | @sys.time |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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
                    "Cookie":"pgv_pvid=9341; qqmusic_uin=46612; qqmusic_key=6883697127; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481198009777",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}

```

#### Play {#13Play}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| date | @sys.date |  |
| name | @sys.entity.media_two_person_act |  |
| peri | @sys.entity.time_period |  |
| repeat | @sys.entity.media_repeat |  |
| time | @sys.time |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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
                    "Cookie":"pgv_pvid=15; qqmusic_uin=51506; qqmusic_key=7158736728; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481198010275",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}

```

#### Play {#14Play}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| date | @sys.date |  |
| name | @sys.entity.media_whys |  |
| peri | @sys.entity.time_period |  |
| repeat | @sys.entity.media_repeat |  |
| time | @sys.time |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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
                    "Cookie":"pgv_pvid=1967; qqmusic_uin=97244; qqmusic_key=5968330277; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481198010724",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}

```

#### Play {#15Play}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| date | @sys.date |  |
| name | @sys.entity.media_yueopera |  |
| peri | @sys.entity.time_period |  |
| repeat | @sys.entity.media_repeat |  |
| time | @sys.time |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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
                    "Cookie":"pgv_pvid=6629; qqmusic_uin=63157; qqmusic_key=4484533654; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481198011246",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}

```

#### Play {#16Play}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| date | @sys.date |  |
| keyword | @sys.entity.media_music_keyword_strong |  |
| name | @sys.entity.media_song_strong |  |
| peri | @sys.entity.time_period |  |
| repeat | @sys.entity.media_repeat |  |
| time | @sys.time |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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
                    "Cookie":"pgv_pvid=2722; qqmusic_uin=60027; qqmusic_key=6604884907; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481198011766",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}

```

#### Play {#17Play}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| artist | @sys.entity.media_singer |  |
| fuz_name | @sys.any |  |
| keyword | @sys.entity.media_music_keyword |  |
| name | @sys.entity.media_song_strong |  |
| repeat | @sys.entity.media_repeat |  |
| singer | @sys.entity.media_singer |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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
                    "Cookie":"pgv_pvid=8567; qqmusic_uin=41043; qqmusic_key=4292502283; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481198012311",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}

```

#### Play {#18Play}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| artist | @sys.entity.media_singer |  |
| keyword | @sys.entity.media_music_keyword |  |
| name | @sys.entity.media_song |  |
| repeat | @sys.entity.media_repeat |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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
                    "Cookie":"pgv_pvid=3516; qqmusic_uin=64338; qqmusic_key=6063108308; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481198012816",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}

```

#### Prev {#19Prev}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Next {#20Next}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Pause {#21Pause}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Resume {#22Resume}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| name |  |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Exit {#23Exit}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Resume {#24Resume}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| name | @sys.entity.media_childsong |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Resume {#25Resume}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| name | @sys.entity.media_story |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Resume {#26Resume}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| name | @sys.entity.media_sketch |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Resume {#27Resume}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| name | @sys.entity.media_crosstalk |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Resume {#28Resume}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| name | @sys.entity.media_joke |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Resume {#29Resume}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| name | @sys.entity.media_storytelling |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Resume {#30Resume}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| name | @sys.entity.media_huangmeixi |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Resume {#31Resume}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| name | @sys.entity.media_two_person_act |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Resume {#32Resume}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| name | @sys.entity.media_yuOpera |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Resume {#33Resume}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| name | @sys.entity.media_whys |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Resume {#34Resume}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| name | @sys.entity.media_yueopera |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Resume {#35Resume}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| artist | @sys.entity.media_poetry_author |  |
| name | @sys.entity.media_poetry_title |  |
| type | @sys.entity.media_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Play {#36Play}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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
                    "Cookie":"pgv_pvid=384; qqmusic_uin=90958; qqmusic_key=5995721997; qqmusic_fromtag=0"
                }
            },
            "image":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000040aH1l3ykBRh.jpg?max_age=2592000",
            "artist":"刘德华",
            "start":0,
            "triggerId":null,
            "trigger":"voice",
            "sid":"1178058206-1481198013333",
            "keywords":null,
            "audio":"http://stream11.qqmusic.qq.com/134838724.mp3",
            "type":"MUSIC"
        },
        "hint":"准备播放"
    }
}

```

