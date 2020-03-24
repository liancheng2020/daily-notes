#### 冒泡排序

```javascript
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

#### 选择排序

```javascript

```

#### 数组去重

```javascript
    var array = [12, 45, 45, 32, 4, 8, 12, 4, 18];
    var arr = [];
    for (var i=0; i<array.length; i++) {
        if (arr.indexOf(array[i]) < 0) {
            arr.push(array[i]);
        }
    }
    for (var x in arr) {
        console.log(arr[x]);
    }
```
