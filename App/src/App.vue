<script>
import { SpeedInsights } from '@vercel/speed-insights/vue';
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
    AppHeader,
    TodosDoneCheck,
    TodoList,
    AppFooter,
    SpeedInsights,
    Analytics
  }
};
</script>

<template>
  <speed-insights />
  <app-header />
  <body class="container">
    <todo-list />
  </body>
  <app-footer />
  <analytics />
</template>

<style>

</style>
