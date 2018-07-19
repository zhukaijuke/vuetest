<template>
  <div id="app">
    <h1>{{ title }}</h1>
    <ul class="todos">
      <li v-for="(todo,index) in todos" :id="index" :class="{'checked':todo.done}">
        <label>{{ index + 1 }}.{{ todo.value }}</label>
      </li>
    </ul>
  </div>
</template>

<script>
  import './assets/site.less'
  import './assets/todos.less'

  export default {
    name: 'App',
    data () {
      return {
        title: 'vue-todos',
        todos: [
          { value: '阅读一本关于前端开发的书', done: false },
          { value: '补充样列代码', done: true },
          { value: '写心得', done: false }
        ]
      }
    }
  }
</script>

<style>
</style>
