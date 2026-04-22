<script>
  
import { Analytics } from '@vercel/analytics/vue';
import AppHeader from './components/AppHeader.vue';
import TodosDoneCheck from './components/TodosDoneCheck.vue';
import TodoList from './components/TodoList.vue';
import AppFooter from './components/AppFooter.vue';
import { SpeedInsights } from '@vercel/speed-insights/vue';


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
    AppFooter,
    SpeedInsights
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
  <SpeedInsights />

</template>

<style>

</style>
