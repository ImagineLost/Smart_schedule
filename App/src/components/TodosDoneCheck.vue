<script>
export default {
  props: {
      totalDone: Number
  }
};
</script>

<template>
  <div class="container">
    <div class="d-flex align-items-center flex-column mb-3">
      <h3>Выполненные задачи</h3>
      <span class="badge bg-success">Всего выполненных задач: {{ totalDone }}</span>
    </div>
    <div class="text-align-center" v-if="totalDone === 0">
      <p class="fw-bold">Пока нет выполненных задач. Очень жаль, но не сдавайтесь, продолжайте работать над своими целями!</p>
    </div>
    <div class="text-align-center" v-if="totalDone <= 10 && totalDone > 0">
      <p class="fw-bold">Отличная работа! Вы уже выполнили {{ totalDone }} задач. Продолжайте в том же духе, и вы достигнете величайших высот</p>
    </div>
    <div class="text-align-center" v-if="totalDone > 10">
      <p class="fw-bold">Вы выполнили {{ totalDone }} задач!!!!! Да вы просто бог мультитакскинга</p>
    </div>
  </div>
</template>