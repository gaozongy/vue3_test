<template>
  <h1>个人信息</h1>
  <h3>姓名：{{name}}</h3>
  <h3>年龄：{{age}}</h3>
  <h3>性别：{{sex}}</h3>
  <button @click="sayHello">说话(vue3所配置的sayHello)</button>
  <br>
  <br>
  <button @click="sayWelcome">说话(vue2所配置的sayWelcome)</button>
  <br>
  <br>
  <button @click="test1">测试一下在vue2的配置中读取vue3的数据、方法</button>
  <br>
  <br>
  <button @click="test2">测试一下在vue3的setup配置中读取vue2的数据、方法</button>
</template>

<script>
// import {h} from 'vue'
export default {
  //此处只是测试一下setup，暂时不考虑响应式的问题
  name: 'App',

  data() {
    return {
      sex:'男'
    }
  },
  methods: {
    sayWelcome() {
      alert('欢迎来到尚硅谷学习！')
    },
    test1() {
      console.log(this.sex)
      console.log(this.name)
      console.log(this.age)
      console.log(this.sayHello)
    }
  },

  setup() {
    //数据
    let name = '张三'
    let age = 18

    //方法
    function sayHello() {
      alert(`我叫${name},我${age}岁了,你好啊`)
    }

    function test2() {
      console.log(name)
      console.log(age)
      console.log(sayHello)
      console.log(this.sex)
      console.log(this.sayWelcome)
    }

    //返回一个对象（常用）
    return {
      name,
      age,
      sayHello,
      test2
    }

    //返回一个函数（渲染函数）
    // return ()=> h('h1','尚硅谷')
  }
}
</script>

