<script>
  
import { Analytics } from '@vercel/analytics/vue';
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
    Analytics,
    AppHeader,
    TodosDoneCheck,
    TodoList,
    AppFooter
  }
};
</script>

<template>
  <Analytics />
  <app-header />
  <body class="container">
    <todo-list />
  </body>
  <app-footer />

</template>

<style>

</style>
