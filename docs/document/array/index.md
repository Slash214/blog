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
