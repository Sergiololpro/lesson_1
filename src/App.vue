<template>
  <div id="app">
    <div class="header">
      <div class="wrapper wrapper-header">
        <div class="header__title">Lesson 1</div>
      </div>
    </div>
    <div class="wrapper">
      <reviews/>
    </div>
  </div>
</template>

<script>
import reviews from '@/components/reviews.vue'

export default {
  name: 'app',
  components: {
    reviews
  }
}
</script>

<style>

</style>
