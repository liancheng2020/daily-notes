#### 冒泡排序

```
    let bubbleSort = function(arr) {
        let i, j, temp
        for (i = 0; i < arr.length; i++) {
            for (j = i + 1; j < arr.length; j++) {
                if (arr[i] > arr[j]) {
                    temp = arr[i]
                    arr[i] = arr[j]
                    arr[j] = temp
                }
            }
        }
        return arr
    }
```

#### 选择排序

```
    let selectSort = function(arr) {
        let i, j, temp, min
        for (i = 0; i < arr.length - 1; i++) {
            min = i
            for (j = i+1; j < arr.length; j++) {
                if (arr[min] > arr[j]) {
                    min = j
                }
            }
            temp = arr[i]
            arr[i] = arr[min]
            arr[min] = temp
        }
        return arr
    }
```

#### 快速排序
```
    let quickSort = function(arr) {
        if (arr.length <= 1) { 
            return arr 
        }
        let pivotIndex = Math.floor(arr.length / 2)
        let pivot = arr.splice(pivotIndex, 1)[0]
        let left = [], right = []
        for (let i = 0; i < arr.length; i++) {
            if (arr[i] < pivot) {
                left.push(arr[i])
            } else {
                right.push(arr[i])
            }
        }
        return quickSort(left).concat([pivot], quickSort(right))
    }
```

#### 插入排序
```
    let insertSort = function(arr) {
        let i, j, temp
        for (i = 0; i < arr.length; i++) {
            temp = arr[i]
            for (j = i-1; j > -1 && arr[j] > temp; j--) {
                arr[j+1] = arr[j]
            }
            arr[j+1] = temp
        }
        return arr
    }
```

#### 数组去重

```
    let arr1 = [12, 45, 45, 32, 4, 8, 12, 4, 18], arr2 = []
    for (let i = 0; i < arr1.length; i++) {
        if (arr2.indexOf(arr1[i]) < 0) {
            arr2.push(arr1[i])
        }
    }
    console.log(arr2)  // 输出[12, 45, 32, 4, 8, 18]
```

#### indexOf 去重

```
    let arr = [12, 45, 45, 32, 4, 8, 12, 4, 18]
    arr = arr.filter((item, index) => arr.indexOf(item) === index)

    console.log(arr)  // 输出输出[12, 45, 32, 4, 8, 18]
```

#### 对象数组去重

```
    let array = [
        { id: 1001, name: '名称1001'},
        { id: 1002, name: '名称1002'},
        { id: 1001, name: '名称1001'},
    ]
    const arr1: string[] = []  // 去重后的数组id集合
    const arr2: any[] = []     // 去重后的对象数组
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

#### 排序去重

```
    let array = [1, 2, 1, 1, '1']
    function unique(array) {
        return array.concat().sort().filter(function(item, index, array){
            return !index || item !== array[index - 1]
        })
    }
    unique(array)  // 输出[1, '1', 2]
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

#### 函数柯里化

- 只传递给函数一部分参数来调用它，让它返回一个函数去处理剩下的参数；
- 每次调用函数时，它只接受一部分参数，并返回一个函数，直到传递所有参数为止；

```
    const add = (x, y) => x+y
    add(1, 2)  // 输出3

    const add = x => y => x+y
    add(1)(2)  // 输出3

    const add = x => y => z => x+y+z
    add(1)(2)(3)  // 输出6 
```

#### 斐波那契数列-递归

```
    function fn(n) {
        return n < 2 ? 1 : fn(n-1) + fn(n-2)
    }
    console.log(fn(0), fn(1), fn(2), fn(3), fn(4), fn(5))  // 输出1, 1, 2, 3, 5, 8
```

#### 对象数组排序
```
    const arr = [
        { id: 1001, name: '名称1001'},
        { id: 1002, name: '名称1002'},
        { id: 1001, name: '名称1001'},
    ]
   
    arr.sort((a, b) => { return a.id - b.id })  // 按照id-升序排序
    arr.sort((a, b) => { return b.id - a.id })  // 按照id-降序排序
```

#### 将一个非负整数数组里的所有数字拼接，打印出能拼接出的所有数字中最小的那个
```
    const minNumber = function(nums) {
        nums = nums.sort((a, b) => {
            return Number(String(a) + String(b)) - Number(String(b) + String(a))
        })
        return nums.join('')
    }
```

#### 浅拷贝（for循环）

```
    // 浅拷贝的实现
    function shallowCopy(object) {
        // 只拷贝对象
        if (!object || typeof object !== "object") return;

        // 根据 object 的类型判断是新建一个数组还是对象
        let newObject = Array.isArray(object) ? [] : {};

        // 遍历 object，并且判断是 object 的属性才拷贝
        for (let key in object) {
            if (object.hasOwnProperty(key)) {
                newObject[key] = object[key];
            }
        }

        return newObject;
    }
```

#### 深拷贝（递归）

```
    // 深拷贝的实现
    function deepCopy(object) {
        if (!object || typeof object !== "object") return;

        let newObject = Array.isArray(object) ? [] : {};

        for (let key in object) {
            if (object.hasOwnProperty(key)) {
                newObject[key] =
                    typeof object[key] === "object" ? deepCopy(object[key]) : object[key];
            }
        }

        return newObject;
    }
```

