<script>
  
import AppHeader from './components/AppHeader.vue';
import TodosDoneCheck from './components/TodosDoneCheck.vue';
import TodoList from './components/TodoList.vue';
import AppFooter from './components/AppFooter.vue';


export default {
  data() {
    return {
    }
  },
  components: {
    AppHeader,
    TodosDoneCheck,
    TodoList,
    AppFooter
  }
};
</script>

<template>
  <app-header />
  <body class="container">
    <todo-list />
  </body>
  <app-footer />

</template>

<style>

</style>
