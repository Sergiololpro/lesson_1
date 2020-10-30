<template>
  <div class="revoewList__wrp">
    <div
      v-for="(review, index) in getReviewsList"
      :key="index"
      class="revoewList"
    >
      <div class="revoewList__title">{{ review.name }}</div>
      <div class="revoewList__text">{{ review.text }}</div>
      <div class="revoewList__date">{{ getDate(review.date) }}</div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'reviewsList',
  computed: {
    getReviewsList() {
      return this.$store.state.list
    }
  },
  
  methods: {
    getDate(date) {
      return new Date(date).getDate() + "." + (new Date(date).getMonth() + 1) + "." + new Date(date).getFullYear()
    }
  }
}
</script>

<style lang="sass">
.revoewList__wrp
  max-width: 400px
  margin: 0 0 50px

.revoewList
  border-bottom: 1px solid #322f31
  position: relative
  padding: 0 0 10px
  margin: 0 0 30px

.revoewList__title
  font-size: 18px
  font-weight: 500
  margin: 0 0 4px

.revoewList__text
  font-size: 14px
  line-height: 200%

.revoewList__date
  font-size: 14px
  color: #797979
  position: absolute
  right: 0
  top: 0
</style>
