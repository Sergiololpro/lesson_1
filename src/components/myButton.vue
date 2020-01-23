<template>
  <button
    v-text="text"
    @click="addComment()"
    class="myButton"
  />
</template>

<script>
export default {
  name: 'myButton',
  props: {
    text: {
      type: String,
      required: false,
      default: () => false
    }
  },

  methods: {
    addComment() {
      this.$emit('myClick')
    }
  }
}
</script>

<style lang="sass">
.myButton
  width: 200px
  height: 44px
  background: #77a44b
  font-size: 14px
  color: #fff
  margin: 20px 0 0
</style>
