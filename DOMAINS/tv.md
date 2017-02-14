## TV

```
主要用于电视的换台换源
```
* [Channel](#Channel)
* [Source](#Source)

#### TV: Channel {#Channel}

---
```
换台
```

* _Data_

| Name | Data type | Required/Optional | Description | Request examples |
| :---: | :---: | :---: |:---: |:---: |
| name | string | optional | 名称换台 | 切换到中央一台(name=中央一台) |
| value | int | optional | 数字换台 | 切换到18频道(value=18) |

#### TV: Source {#Source}

---
```
换源
```
* _Data_

| Name | Data type | Required/Optional | Description | Request examples |
| :---: | :---: | :---: |:---: |:---: |
| type | string | optional | 换源 | 换到数字频道(type=数字频道) |

