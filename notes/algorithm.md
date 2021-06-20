#### 冒泡排序

```
    let arr = [12, 34, 3, 24, 78, 90, 16, 45], temp = 0
    for (let i=0; i < arr.length; i++) {
        for (let j= i+1; j < arr.length; j++) {
            if (arr[i] > arr[j]) {
                temp = arr[i]
                arr[i] = arr[j]
                arr[j] = temp
            }
        }
    }
    console.log(arr)  // 输出[3, 12, 16, 24, 34, 45, 78, 90]
```

```
    let arr = [12, 34, 3, 24, 78, 90, 16, 45], temp = 0
    for(let i=0; i<arr.length; i++) {
        for(let j=arr.length-1; j>=i; j--)  // for(let j=0; j<arr.length-1-i; j++)
        {
            if (arr[j] > arr[j+1]) {
                temp = arr[j]
                arr[j] = arr[j+1]
                arr[j+1] = temp
            }
        }
    }
    console.log(arr)  // 输出[3, 12, 16, 24, 34, 45, 78, 90]
```

#### 选择排序

```
    let arr = [12, 34, 3, 24, 78, 90, 16, 45], temp = 0
    for (let i=0; i<arr.length-1; i++) {
        let min = i;
        for (var j=i+1; j<arr.length; j++) {
            if (arr[j] < arr[min]) {
                min = j
            }
        }
        temp = arr[i]
        arr[i] = arr[min]
        arr[min] = temp
    }
    console.log(arr)  // 输出[3, 12, 16, 24, 34, 45, 78, 90]
```

#### 数组去重

```
    var array = [12, 45, 45, 32, 4, 8, 12, 4, 18]
    var arr = []
    for (var i=0; i<array.length; i++) {
        if (arr.indexOf(array[i]) < 0) {
            arr.push(array[i])
        }
    }
    console.log(arr)  // 输出[12, 45, 32, 8, 18]
```
#### 对象数组去重

```
    let array = [
        { id: 1001, name: '名称1001'},
        { id: 1002, name: '名称1002'},
        { id: 1001, name: '名称1001'},
    ]
    const arr1: string[] = [] // 去重后的数组id集合
    const arr2: any[] = [] // 去重后的对象数组
    array.forEach((item: any) => {
        if (arr1.indexOf(item.id) === -1) {
            arr1.push(item.id)
            arr2.push(item)
        }
    })
    console.log(arr1)  // 输出[1001, 1002]
    console.log(arr2)  // 输出[{ id: 1001, name: '名称1001'}, { id: 1002, name: '名称1002'}]
```

#### ES6 new Set方法数组去重

```
    const arr1 = [10, 20, 30, 10, 12, 20]
    const arr2 = [...new Set(arr1)]
    console.log(arr2)  // 输出[10, 20, 30, 12]
```

#### reduce方法-数组去重

```
    const arr1 = [10, 20, 30, 10, 12, 20]
    const arr2 = arr1.reduce((pre, cur) => {
        if (!pre.includes(cur)) {
            return pre.concat(cur)
        } else {
            return pre
        }
    }, [])
    console.log(arr2)  // 输出[10, 20, 30, 12]
```

#### 数组扁平化-flat()方法

- 不传参数时，默认“拉平”一层；
- 传入一个整数参数，整数即“拉平”的层数；
- 数组作为参数时，无论多少层嵌套，都会转为一维数组；
- 传入 <=0 的整数将返回原数组，不“拉平”；

```
    const arr = [10, 20, [12, 36], [12, [20, 30]], 50]
    arr.flat()   // 输出[10, 20, 12, 36, 12, [20, 30], 50]
    arr.flat(2)  // 输出[10, 20, 12, 36, 12, 20, 30, 50]
    arr.flat(3)  // 输出[10, 20, 12, 36, 12, 20, 30, 50]
    arr.flat(-1)   // 输出[10, 20, [12, 36], [12, [20, 30]], 50]
    flat([10, 20, 30])        // 输出[10, 20, 30]
    flat([10, [20, 30], 36])  // 输出[10, 20, 30, 36]

    const array = [1, 2, [10, 20, [12, [10, 20, 30]]], 50, "string", { name: "名称" }]
    const flatArr = function() {
        return array.reduce((pre, cur) => {
            return pre.concat(Array.isArray(cur) ? flat(cur) : cur)
        }, [])
    }
    flatArr()  // 输出[1, 2, 10, 20, 12, 10, 20, 30, 50, "string", {name: "名称"}]
```