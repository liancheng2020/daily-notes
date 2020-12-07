#### 表情包校验

```git
value = value
      .replace(
        /\uD83C[\uDF00-\uDFFF]|\uD83D[\uDC00-\uDE4F]|[\uD800-\uDBFF]|[\uDC00-\uDFFF]|[^\u0020-\u007E\u00A0-\u00BE\u2E80-\uA4CF\uF900-\uFAFF\uFE30-\uFE4F\uFF00-\uFFEF\u0080-\u009F\u2000-\u201f\u2026\u2022\u20ac\r\n]/g,
        ''
      )
      .trim()
```

#### 只允许输入正整数

```git
value = value.replace(/[^\d]/g, '')
```

#### 手机号校验正则表达式

```git
regex = /^1[3-9][0-9]{9}$/
```
