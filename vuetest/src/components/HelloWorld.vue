<template>
    <div id="HelloWorld">
        <h1>{{ title }}</h1>
        <ul class="todos">
            <li v-for="(todo,index) in todos" :id="index" :class="{'checked':todo.done}">
                <label>{{ index + 1 }}.{{ todo.value }}</label>
                <time>{{ todo.created | date }}</time>
            </li>
        </ul>
    </div>
</template>

<script>
    import moment from 'moment'
    import 'moment/locale/zh-cn'

    moment.locale('zh-cn')

    export default {
        name: 'HelloWorld',
        data() {
            return {
                title: 'vue-todos',
                todos: [
                    {value: '阅读一本关于前端开发的书', done: false, created: Date.now()},
                    {value: '补充样列代码', done: true, created: Date.now() + 300000},
                    {value: '写心得', done: false, created: Date.now() - 300000}
                ]
            }
        },
        filters: {
            date(val) {
                return moment(val).calendar();
            }
        }
    }
</script>

<style>
</style>
