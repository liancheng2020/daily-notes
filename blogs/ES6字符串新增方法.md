#### String 实例方法

- includes()
  - 返回布尔值，表示是否找到了参数字符串；
- startsWith()
  - 返回布尔值，表示参数字符串是否在原字符串的头部；
- endsWith()
  - 返回布尔值，表示参数字符串是否在原字符串的尾部；

- 三个方法都支持第二个参数，表示开始搜索的位置；
- 使用第二个参数n时，endsWith的行为与其他两个方法有所不同，它针对前n个字符，而其他两个方法针对从第n个位置直到字符串结束；

- search()
  - 查找匹配的字符串，返回匹配的位置索引，失败时返回-1；
  
- repeat()
  - 返回一个新字符串，表示将原字符串重复n次；
  - 参数如果是小数，会被取整；
  - 参数是负数或Infinity，会报错；
```
  const str = 'abc'

  str.repeat(3)    // 'abcabcabc'
  str.repeat(1.8)  // 'abcabc'
  str.repeat(2.5)  // 'abcabc'
  str.repeat(-1)   // RangeError报错
```

- trimStart()、trimEnd()
  - trimStart()消除字符串头部的空格，trimEnd()消除尾部的空格；
  - 它们返回的都是新字符串，不会修改原始字符串；
  - 浏览器还部署了额外的两个方法，trimLeft()是trimStart()的别名，trimRight()是trimEnd()的别名；

- replaceAll()
  - 一次性替换所有匹配；
  - 用法与replace()相同，返回一个新字符串，不会改变原字符串；
```
  const str = 'aabbcc'
  
  str.replace('b', '_')      // 'aa_bcc'
  str.replace(/b/g, '_')     // 'aa__cc'
  str.replaceAll('b', '_')   // 'aa__cc'
```