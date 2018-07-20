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
  </div>
</template>

<script>
  import '@/assets/site.less'
  import '@/assets/todos.less'

  export default {
    name: 'App'
  }
</script>

<style>
  ul,li{ margin: 0px; padding: 0px; list-style-type: none;}
  li:hover{ color:#F60; }
  .point{ cursor: pointer }

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
  .active{ color: red; }
</style>
