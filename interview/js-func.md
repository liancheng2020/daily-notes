```
// new
function new (fn, ...args) {
    let obj = Object.create(fn.prototype)
    let res = fn.apply(obj, args)
    return res instanceof Object ? res : obj
}

// instanceof
function instanceof (left, right) {
    while (true) {
        if (left === null) return false
        if (left.__proto === right.prototype) return true
        left = left.__proto__
    }
}

// deep
function deep (obj) {
    if (!obj || typeof obj !== 'object') return
    let newObj = Array.isArray(obj) ? [] : {}
    for (let key in obj) {
        if (obj.hasOwnproperty(key)) {
            newObj[key] = typeof obj[key] === 'object' ? deep(obj[key]) : obj[key]
        }
    }
    return newObj
}

// shallow
function shallow (obj) {
    if (!obj || typeof obj !== 'object') return
    let newObj = Array.isArray(obj) ? [] : {}
    for (let key in obj) {
        if (obj.hasOwnproperty(key)) {
            newObj[key] = obj[key]
        }
    }
    return newObj
}

// debounce
function debounce (fn, delay) {
    let timeout;
    return function (...args) {
        clearTimeout(timeout)
        timeout = setTimout(() => {
            fn.apply(this, args)
        }, delay)
    }
}

// throttle
function throttle (fn, delay) {
    let last = 0
    return function (...args) {
        let now = Date.now()
        if (now - last >= delay) {
            fn.apply(this, args)
            last = now
        }
    }
}

// call
function call (context, ...args) {
    const fn = Symbol('fn')
    context = context || window
    context[fn] = this
    const res = context[fn](...args)
    delete context[fn]
    return res
}

// apply
function apply(context, args) {
    const fn = Symbol('fn')
    context = context || window
    context[fn] = this
    const res = context[fn](...args)
    delete context[fn]
    return res
}

// bind
function bind (context, ...args) {
    const ogiginFn = this
    return function (...innerArgs) {
        const combinArgs = args.concat(innerArgs)
        return originFn.apply(context, combinArgs)
    }
}

```
