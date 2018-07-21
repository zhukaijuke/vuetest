<template>
    <div id="app">
        <ul class="point">
            <router-link :to="{ name: 'Admin' }" tag="li" exact>
                <div><p>admin页面</p></div>
            </router-link>
            <router-link :to="{ name: 'HelloWorld' }" tag="li" exact>
                <div><p>todos页面</p></div>
            </router-link>
        </ul>
        <transition name="slide-fade">
            <router-view/>
        </transition>
        <other parent-msg="来自父元素的Msg">
            <div slot="a">插入slot-a</div>
            <div>其他元素</div>
        </other>
        <input type="text" v-focus name="z" v-model="myInput" ref="myInput"/><button @click="alertInput">点击</button>
    </div>
</template>

<script>
    import './assets/site.less'
    import './assets/todos.less'
    import Vue from 'vue'
    import Other from "./components/other";

    Vue.directive('focus', {
        inserted: function (el) {
            el.focus();
        }
    });

    export default {
        name: 'App',
        components: {Other},
        data() {
            return {
                myInput: ''
            }
        },
        methods: {
            alertInput: function () {
                if (this.myInput !== '') {
                    alert(this.myInput);
                }
                this.myInput = '';
                this.$refs.myInput.focus();
            }
        }
    }
</script>

<style>
    ul, li {
        margin: 0px;
        padding: 0px;
        list-style-type: none;
    }

    li:hover {
        color: #F60;
    }

    .point {
        cursor: pointer
    }

    .slide-fade-enter-active {
        transition: all .3s ease;
    }

    .slide-fade-leave-active {
        transition: all .3s cubic-bezier(1.0, 0.5, 0.8, 1.0);
    }

    .slide-fade-enter, .slide-fade-leave-active {
        transform: translateX(-430px);
        opacity: 0;
    }

    .active {
        color: red;
    }
</style>
