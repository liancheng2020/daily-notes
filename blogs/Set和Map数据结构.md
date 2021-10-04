#### Set 数据结构

- ES6 提供了新的数据结构 Set，它类似于数组，但是成员的值都是唯一的，没有重复的值；
- Set 本身是一个构造函数，用来生成 Set 数据结构，不会添加重复的值；
- 向 Set 加入值的时候，不会发生类型转换，所以5和'5'是两个不同的值；
- Array.from方法可以将 Set 结构转为数组；
- Set 结构没有键名，只有键值（或者说键名和键值是同一个值）；
&nbsp;
- add(value)：添加某个值，返回Set对象本身；
- delete(value)：删除某个值，成功返回true，失败返回false；
- has(value)：判断某个值是否在当前Set对象之中，是返回true，否返回false；
- clear()：删除所有的键/值对，没有返回值；
```
  const a = new Set([1, 2, 3])
  const b = new Set([4, 3, 2])
  const unionSet = new Set(...a, ...b)  // 并集 {1, 2, 3, 4} 
  const interSet = new Set([...a].filter(x => b.has(x)))  // 交集 {2, 3}

  const c = new Set('aaabbbbc')
  const duplSet = [...c].join('')  // 字符串去重 'abc'
```

- Set 结构的实例有四个遍历方法，可以用于遍历成员：
  - keys()：返回键名的遍历器；
  - values()：返回键值的遍历器；
  - entries()：返回键值对的遍历器；
  - forEach()：使用回调函数遍历每个成员；
```
  let set = new Set(['Red', Green', 'Blue'])
  const arr1 = arr.keys()
  const arr2 = arr.values() 
  const arr3 = arr.entries() 

  for (let item of arr1) {
    console.log(item)
  }
  // 输出结果：Red Green Blue

  for (let item of arr2) {
    console.log(item)
  }
  // 输出结果：Red Green Blue

  for (let item of arr3) {
    console.log(item);
  }
  // 输出结果：['Red', 'Red'] ['Green', 'Green'] ['Blue', 'Blue']

  set.forEach((item) => {
    console.log(item)
  })
  // 输出结果：Red Green Blue
```

#### Map 数据结构

- ES6 提供了 Map 数据结构，它类似于对象，也是键值对的集合；
- Object 结构提供了“字符串—值”的对应，Map 结构提供了“值—值”的对应，是一种更完善的 Hash 结构实现；
- Map 结构转为数组结构，比较快速的方法是使用扩展运算符（...）；
&nbsp;
- size属性：返回 Map 结构的成员总数；
- set(key, value)：置键名key对应的键值为value，然后返回整个 Map 结构；
- get(key)：读取key对应的键值，如果找不到key，返回undefined；
- has(key)：判断某个键是否在当前 Map 对象中，是返回true，否返回false；
- delete(key)：删除某个键，删除成功返回true，失败返回false；
- clear()：清除所有成员，没有返回值；
```
  const map = new Map()
  map.set('foo', true)
  map.set('bar', false)

  map.size   // 2
  map.get('hello')  // undefined
  map.get('foo')    // true
```

- Map 结构提供三个遍历器生成函数和一个遍历方法：
  - keys()：返回键名的遍历器；
  - values()：返回键值的遍历器；
  - entries()：返回所有成员的遍历器；
  - forEach()：遍历 Map 的所有成员；
```
  const map = new Map([
    [1, 'one'],
    [2, 'two'],
    [3, 'three'],
  ])

  [...map]            // [[1,'one'], [2, 'two'], [3, 'three']]
  [...map.keys()]     // [1, 2, 3]
  [...map.values()]   // ['one', 'two', 'three']
  [...map.entries()]  // [[1,'one'], [2, 'two'], [3, 'three']]
````