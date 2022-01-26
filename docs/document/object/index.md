# 对象

> 以下为我学习总结的一些Object对象的方法


### 定义
>  对象 [] 表示属性的key值是一个变量
```
let name = '爱仕达'
let age = 43
let s = 'school'
let obj = {
    name,
    age,
    [s]: 'asdas',
    study() {
        console.log("我爱你")
    }
}
obj.study()
// console.log(obj)

<!-- 判断两个值是否相等 -->
console.log(Object.is(2, '2'))  // false
console.log(Object.is(NaN, NaN)) // true
console.log(Object.is(+0, -0))


<!-- 判断对象引用地址是否相等  ---如引用一样才相等 -->
let obj1 = { name: 'xdsd', age: 34  }
let obj2 = { name: 'xdsd', age: 34  }

console.log(obj1 == obj2)
let obj2 = obj1
console.log(Object.is(obj1 , obj2))


<!-- 扩展运算符 和 Object.assign() -->

let x = {
    a: 3,
    b: 5
}

let y = {...x}  // copy 对象
let y = {
    c: 79,
    a: 6
}
Object.assign() // 作用合并对象  第一个参数：目标对象  后面覆盖前面的值
Object.assign(y, x)
console.log(y)
console.log('aaa' in x)

in 可用在数组 对象 上
let arr = [1,2,3]
console.log(2 in arr)  // 3表示下标为3的是否存在  数组不存在返回false

let obj = {
    name: 'asdsa',
    age: 74,
    school: '3213'
}

<!-- 对象遍历的方式 -->

1 for (let key in obj) {
    console.log(key, obj[key])
}

<!-- es6方法 -->
2 Object.keys(obj).forEach(key => {
    console.log(key, obj[key])
})

3 Object.getOwnPropertyNames(obj).forEach(key => {
    console.log(key, obj[key])
})

4 Reflect.ownKeys(obj).forEach(key => {
    console.log(key, obj[key])
})
``` 