#### 冒泡排序

```
    var arr = [12, 34, 3, 24, 78, 90, 16, 45], temp = 0;
    for (var i=0; i<arr.length; i++) {
        for (var j=i+1; j<arr.length; j++) {
            if (arr[i] > arr[j]) {
                temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
    }
    for (var x in arr) {
        console.log(arr[x]);
    }
```

```
    var arr = [12,34,3,24,78,90,16,45], temp = 0;
    for(var i=0; i<arr.length; i++)
    {
        for(var j=arr.length-1; j>=i; j--)   //for(var j=0; j<arr.length-1-i; j++)
        {
            if(arr[j] > arr[j+1])
            {
                temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
    }
    for(var x in arr)
    {
        console.log(arr[x]);
    }
```

#### 选择排序

```
    var arr = [12, 34, 3, 24, 78, 90, 16, 45], temp = 0;
    for (var i=0; i<arr.length-1; i++) {
        var min = i;
        for (var j=i+1; j<arr.length; j++) {
            if (arr[j] < arr[min]) {
                min = j;
            }
        }
        temp = arr[i];
        arr[i] = arr[min];
        arr[min] = temp;
    }
    for (var x in arr) {
        console.log(arr[x]);
    }
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
    for (var x in arr) {
        console.log(arr[x])
    }
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
