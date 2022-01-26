# 数组的操作方法合集

###  合并数组
> concat() 方法用于连接两个或多个数组。该方法不会改变现有的数组，仅会返回被连接数组的一个副本。
```
let a = [1,2,3], b = [2,3,5]
let total = a.concat(b)   
新语法   
let all = [...a,...b]
```

###  数组插入元素
> push() 方法可向数组的末尾添加一个或多个元素，并返回新的长度。末尾添加，返回的是长度，会改变原数组。
```push()

const a = []   
a.push(1)   

```

### shift() 方法
> shift() 方法用于把数组的第一个元素从其中删除，并返回第一个元素的值。返回第一个元素，改变原数组。
```
const arr = [2,3,5]
console.log(arr.shift())  // 2   
console.log(arr)  // 3, 5
```

### unshift()
> unshift() 方法可向数组的开头添加一个或更多元素，并返回新的长度。返回新长度，改变原数组。
```
var arr = [2,3,4,5];
console.log(arr.unshift(3,6)); //6
console.log(arr); //[3, 6, 2, 3, 4, 5]
```


### for 循环
> 1：for 循环 支持 break, continue   
> let arr = [1, 2, 3, 2, 4]
```
    for (let i = 0; i<arr.length; i++) {
        console.log(arr[i]) // 1,2,3,4
    }
```

> 2：forEach 不支持 break, continue 不能跳出循环 
```
 <!-- 后面方法作为参数 三个参数  1：当前遍历的对象  2：当前遍历对象的索引 3：正在遍历的数组本身 -->
 arr.forEach(function (elem, index, array) {
      console.warn(elem)
      console.error(index)
      console.info(array)
 }) 
```

> 3：map 会遍历数组每一个元素 会返回新数组 并不会改变原数组
```
 let result = arr.map(function(value) {
   value += 1
  console.log(value)
   return value
 }) 

 console.log(arr, result)
```


> 4：filter 过滤 遍历数组 返回新数组 不会修改原数组
```
 新数组的元素经过了筛选 符合的才返回
 let result = arr.filter(function (value) {
      console.log(value)
     return value == 2
 })
 console.log(arr, result)
```


> 5：some 遍历数组里符合条件的值，找到一个符合的都会返回true  并返回 布尔类型的值 true or fasle （不会改变原设置）
```
 let result = arr.some(function (value) {
      console.log(value)
     return value == 4
 })
 console.log(arr, result)
```


> 6：every 检查数组里的每一个元素是否符合条件，符合返回true 否则返回false
```
 let result = arr.every(function (value) {
      console.log(value)
     return value == 2
 })
 console.log(arr, result)
```

> reduce 累加器   
> 两个参数, 1:方法【方法里面有4个值- 1-prev：上一次回调调用的初始值 2-cur 正在处理的数组元素  3-当前处理元素对应的索引  4-原数组】  2：初始值
```
 如下方求合的
 let sum = arr.reduce(function(prev, cur, index, arr){
    return prev + cur 
 }, 0)
 console.log(sum)

 例子 找到数组最大的值
 let max = arr.reduce(function(prev, cur){
   return Math.max(prev, cur)
 })
 console.log(max)

 例子 数组去重
 let result =  arr.reduce(function(prev, cur) {
    idnexOf 不包含返回-1 包含返回下标
   prev.indexOf(cur) == -1 && prev.push(cur)
   return prev
 }, [])

 console.log(result)
```

> for in 不建议遍历数组
```
 for (let index in arr) {
   console.log(index, arr[index])
 }
```

## ES6 遍历数组方法
```
 find  返回第一个通过测试的元素  没找到返回 undefined
 let res = arr.find(function(value) {
   return value == 8
 })

 console.log(arr, res)

 findIndex  返回下标
 let res = arr.findIndex(function(value) {
     return value == 2
   })
  
 console.log(arr, res)


 for of
 for ( let item of arr.values()) {
     console.log(item)
 } 

 获取下标 
 for ( let item of arr.keys()) {
     console.log(item)
 } 


 内容 下标都需要
 for ( let [index,item] of arr.entries()) {
     console.log(index,item)
 } 
```
