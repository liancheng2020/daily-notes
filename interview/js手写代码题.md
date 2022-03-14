1. new 操作符的实现：

```
  function myNew(fn, ...args) {
    let obj = Object.create(fn.prototype);
    let res = fn.call(obj, ...args);
    if (res && (typeof res === "object" || typeof res === "function")) {
      return res;
    }
    return obj;
  }
```

2. instanceof 操作符的实现：

```
  function myInstanceof(left, right) {
    while (true) {
      if (left === null) {
        return false;
      }
      if (left.__proto__ === right.prototype) {
        return true;
      }
      left = left.__proto__;
    }
  }
```

3. call/apply/bind 函数实现：

```
  // call 原理实现
  Function.prototype.myCall = function(thisArg, ...args) {
    const fn = Symbol('fn')        // 声明一个独有的Symbol属性, 防止fn覆盖已有属性
    thisArg = thisArg || window    // 若没有传入this, 默认绑定window对象
    thisArg[fn] = this             // this指向调用call的对象,即我们要改变this指向的函数
    const result = thisArg[fn](...args)  // 执行当前函数
    delete thisArg[fn]             // 删除我们声明的fn属性
    return result                  // 返回函数执行结果
  }

  // apply 原理实现
  Function.prototype.myApply = function(thisArg, args) {
    const fn = Symbol('fn')        // 声明一个独有的Symbol属性, 防止fn覆盖已有属性
    thisArg = thisArg || window    // 若没有传入this, 默认绑定window对象
    thisArg[fn] = this             // this指向调用call的对象,即我们要改变this指向的函数
    const result = thisArg[fn](...args)   // 执行当前函数（此处说明一下：虽然apply()接收的是一个数组，但在调用原函数时，依然要展开参数数组。可以对照原生apply()，原函数接收到展开的参数数组）
    delete thisArg[fn]             // 删除我们声明的fn属性
    return result                  // 返回函数执行结果
  }

  // bind 原理实现
  Function.prototype.myBind = function (thisArg, ...args) {
    var self = this
    var fbound = function () {
      self.apply(this instanceof self ? this : thisArg, args.concat(Array.prototype.slice.call(arguments)))
    }
    fbound.prototype = Object.create(self.prototype);
    return fbound;
  }
```

4. 防抖/节流 函数实现：

```
  // 防抖
  function debounce(fn, delay) {
    let timeout = null
    return function() {
      let context = this
      let args = arguments
      if (timeout) clearTimeout(timeout)
      timeout = setTimeout(() => {
        fn.apply(context, args)
      }, delay)
    }
  }

  // 节流
  function throttle(fn, delay) {
    let timeout = null
    return function() {
      let context = this
      let args = arguments
      if (!timeout) {
        timeout = setTimeout(() => {
          timeout  = null
          fn.apply(context, args)
        }, delay)
      }
    }
  }
```

5. 深/浅拷贝 函数实现：

```
  // 深拷贝（递归）
  function deepCopy(object) {
    if (!object || typeof object !== "object") return;
    let newObject = Array.isArray(object) ? [] : {};
    for (let key in object) {
      if (object.hasOwnProperty(key)) {
        newObject[key] = typeof object[key] === "object" ? deepCopy(object[key]) : object[key];
      }
    }
    return newObject;
  }

  // 浅拷贝（for循环）
  function shallowCopy(object) {
    if (!object || typeof object !== "object") return;
    let newObject = Array.isArray(object) ? [] : {};
    for (let key in object) {
      if (object.hasOwnProperty(key)) {
        newObject[key] = object[key];
      }
    }
    return newObject;
  }
```

6. Promise 函数实现：

```
  function myPromise(constructor){
    let self = this;
    self.status = "pending";    // 定义状态改变前的初始状态
    self.value = undefined;     // 定义状态为resolved的时候的状态
    self.reason = undefined;    // 定义状态为rejected的时候的状态
    function resolve(value) {
      // 两个 === "pending"，保证了状态的改变是不可逆的
      if(self.status === "pending") {
        self.value = value;
        self.status = "resolved";
      }
    }
    function reject(reason) {
      // 两个 === "pending"，保证了状态的改变是不可逆的
      if(self.status === "pending") {
        self.reason = reason;
        self.status = "rejected";
      }
    }
    //捕获构造异常
    try {
      constructor(resolve,reject);
    } catch(e) {
      reject(e);
    }
  }

  myPromise.prototype.then = function(onFullfilled, onRejected) {
    let self = this;
    switch(self.status) {
      case "resolved":
        onFullfilled(self.value);
        break;
      case "rejected":
        onRejected(self.reason);
        break;
      default:       
    }
  }
```
