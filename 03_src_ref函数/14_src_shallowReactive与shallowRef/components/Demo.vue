<template>
  <h4>当前的x值是：{{x}}</h4>
  <button @click="x++">点我x++</button>
  <hr>
  <h4>{{person}}</h4>
  <h2>姓名：{{name}}</h2>
  <h2>年龄：{{age}}</h2>
  <h2>薪水：{{job.j1.salary}}k</h2>
  <button @click="name+='~'">修改姓名</button>
  <button @click="age++">修改年龄</button>
  <button @click="job.j1.salary++">涨薪</button>
</template>

<script>
import {ref,reactive,toRef,toRefs,shallowRef,shallowReactive} from 'vue'
export default {
  name: 'Demo',
  setup() {
    //数据
    // let person = shallowReactive({//只考虑第一层数据的响应式
    let person = reactive({
      name:'张三',
      age:18,
      job:{
        j1:{
          salary:20
        }
      }
    })
    let x = ref(0)
    // let x = shallowRef({
    //   y:0
    // })//不处理对象类型的响应式数据

//返回一个对象（常用）
    return {
      person,
      ...toRefs(person),
      x
    }
  }
}
</script>

