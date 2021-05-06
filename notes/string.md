#### url 参数获取

```
    function getQueryString(data) {
        var reg = new RegExp('(^|&)' + data + '=([^&]*)(&|$)', 'i')
        var r = window.location.search.substr(1).match(reg)
        if (r != null)
            return decodeURI(r[2])
        return null
    }
```

#### 字符串截取

```
    str = str.replace(/\s*/g, '')  // 去除string中的所有空格
    str = str.replace(/\d+/g, '')  // 去除string中的所有数字
    str = str.replace(/[\u4e00-\u9fa5]/g, '')  // 去除string中的所有汉字
    str1 = str1.replace(str2, '')  // 去除str1中包含的str2
```


#### 字符串拆分

```
    str1 = '123a456a789'
    str2 = str1.split('a')  // 将字符串拆分成数组
    str2 = ["123", "456", "789"]
```

