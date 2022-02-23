# Vue踩坑记录
> 学习Vue2时碰到的一些问题  
> version vue2.6 node12.x  vue-cli4

### 路由跳转传参
```
方法一：params 传参
this.$route.push({ name: '', params: {id: item.id }})

@params name --路由里配置的路由名 这里也可以使用path路由路径
@params params --一个对象

通过params传参 在页面获取的时候使用：
this.$route.params.id(对象里面的属性id) 获取到值
【ps: 获取的参数是$route,跳转和传参都是$router】

方法二：路由属性配置传参
this.$router.push({ name: `/index/${item.id}`})

组件对应的路由配置为
{
   path: '/index:id', //组件路径
   name: 'index',     //组件路由名
   component: Index,  //组件模板
}

通过路由属性配置传参我们可以用this.$route.params.id来获取到id的值，
注意this.$router.push方法里面路径带的是值，
路由配置项那里带的是变量名(属性名)来实现的对应；

以上两个方法参数不可见，但是页刷新后就获取不到参数了！！！

方法三：query传参

this.$router.push({ name: '/index', query: {id: item.id} })

// 这个组件对应的路由配置
{
  path: '/index',
  name: 'index',
  component: Index
}

通过query来传参，这种方式可以解决页面刷新参数消失的问题，但参数在路径上是可见的

【通过缓存也可以使用页面路由参数的互传，这是Vue的三种方法】
```

### 页面刷新
```
1：在App.vue配置

// 通过添加v-if去隐藏显示路由实现页面刷新数据重新加载效果
<template>
  <div id="app">
    <router-view v-if="isRouterAlive" />
  </div>
</template>

<script>
export default {
  name: 'App',
  provide() {
    return {
      reload: this.reload
    }
  },
  data() {
    return {
      isRouterAlive: true
    }
  },
  methods: {
    reload() {
      this.isRouterAlive = false
      this.$nextTick(function() {
        this.isRouterAlive = true
      })
    }
  }
}
</script>

2：在需要刷新的页面引入
<script>
 export default {
   inject: ['reload'],
   methods: {
     refresh() {
      // 刷新方法，直接调用写好的刷新函数就可以实现效果
      this.reload()
     },
   }
 }
</script>
```

### keep-alive放弃缓存某一个组件
```
关键代码：exclude="组件的name"
<keep-alive exclude="musiclist">
    <router-view />
</keep-alive>

解释说明：vue2.0版本后，keep-alive内置组件已经封装了两个属性，include和exclude表
示那些组件需要缓存那些组件不需要缓存。

<keep-alive include="test-keep-alive">
  <!-- 将缓存name为test-keep-alive的组件 -->
  <component></component>
</keep-alive>
 
<keep-alive include="a,b">
  <!-- 将缓存name为a或者b的组件，结合动态组件使用 -->
  <component :is="view"></component>
</keep-alive>
 
<!-- 使用正则表达式，需使用v-bind -->
<keep-alive :include="/a|b/">
  <component :is="view"></component>
</keep-alive>
 
<!-- 动态判断 -->
<keep-alive :include="includedComponents">
  <router-view></router-view>
</keep-alive>
 
<keep-alive exclude="test-keep-alive">
  <!-- 将不缓存name为test-keep-alive的组件 -->
  <component></component>
</keep-alive>

```