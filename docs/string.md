#### url 参数获取

```javascript
    function getQueryString(data) {
        var reg = new RegExp("(^|&)" + data + "=([^&]*)(&|$)", "i");
        var r = window.location.search.substr(1).match(reg);
        if (r != null)
            return decodeURI(r[2]);
        return null;
    }

    console("userid: ", getQueryString("userid"))
```

#### 字符串截取

```javascript
    str = str.replace(/\s*/g, ""); //去除string中的所有空格
    str = str.replace(/\d+/g, ""); //去除string中的所有数字
    str = str.replace(/[\u4e00-\u9fa5]/g, ""); //去除string中的所有汉字
    str1 = str1.replace(str2, ""); //去除str1中包含的str2
```
