#### Array方法大全

> - map: 遍历数组，返回回调返回值组成的新数组
>
> - forEach: 无法break，可以用try/catch中throw new Error来停止
>
> - filter: 过滤
>
> - some: 有一项返回true，则整体为true
>
> - every: 有一项返回false，则整体为false
>
> - join: 通过指定连接符生成字符串
>
> - push / pop: 末尾推入和弹出，改变原数组， 返回推入/弹出项
>
> - unshift / shift: 头部推入和弹出，改变原数组，返回操作项
>
> - sort(fn) / reverse: 排序与反转，改变原数组
>
> - concat: 连接数组，不影响原数组， 浅拷贝
>
> - slice(start, end): 返回截断后的新数组，不改变原数组
>
> - splice(start, number, value...): 返回删除元素组成的数组，value 为插入项，改变原数组
>
> - indexOf / lastIndexOf(value, fromIndex): 查找数组项，返回对应的下标
>
> - reduce / reduceRight(fn(prev, cur)， defaultPrev): 两两执行，prev 为上次化简函数的return值，cur 为当前值(从第二项开始)
> 
> - find: 返回数组中符合条件的第一个元素的值，否则返回 undefined
> 
> - findIndex: 返回数组中满足符合条件的第一个元素的索引，否则返回 -1
> 
> - includes: 判断数组中是否包含指定的元素，如果是返回 true，否则返回 false

#### Math()相关方法大全

> - Math.random(): 返回一个0到1之间的随机数
>
> - Math.ceil(): 返回一个大于或等于当前数字的整数
>
> - Math.floor(): 返回一个小于或等于当前数字的整数
>
> - Math.round(): 返回一个四舍五入最接近当前数字的整数
