<template>
  <div>
    <h1 class="reviews__h1">Отзывы</h1>
    <template v-if="showList">
      <reviewsList/>
    </template>
    <template v-else>
      <div class="reviews__text">Отзывов пока нет</div>
    </template>
    <div class="reviews__wrp">
      <h2 class="reviews__h2">Оставить отзыв</h2>
      <myInput
        v-model="name"
        name="name"
        label="Имя"
        placeholder="Введите ваше имя"
        errorText="Имя не введено!"
        :isValidation="formValidation"
      />
      <myInput
        v-model="text"
        name="review"
        label="Отзыв"
        placeholder="Введите ваш отзыв"
        errorText="Отзыв не введен!"
        :isValidation="formValidation"
        :isTextarea="true"
        :isRequired="true"
      />
      <myButton
        text="Добавить отзыв"
        @myClick="addComment"
      />
    </div>
  </div>
</template>

<script>
import myInput from '@/components/myInput.vue'
import myButton from '@/components/myButton.vue'
import reviewsList from '@/components/reviewsList.vue'

export default {
  name: 'reviews',
  components: {
    myInput,
    myButton,
    reviewsList
  },

  data: () => ({
    name: "",
    text: "",
    formValidation: false
  }),

  computed: {
    showList() {
      return this.$store.state.list.length
    }
  },

  methods: {
    addComment() {
      this.formValidation = true;

      if (this.text.length) {
        const reviewItem = {
          name: this.name || "Аноним",
          text: this.text,
          date: new Date()
        }

        this.$store.commit('addReview', reviewItem);
        this.name = "";
        this.text = "";
        this.formValidation = false;
      }
    }
  }
}
</script>

<style lang="sass">
.reviews__wrp
  widtj: 100%
  max-width: 400px

.reviews__h1
  font-size: 32px
  font-weight: 500
  margin: 40px 0 30px

.reviews__h2
  font-size: 22px
  font-weight: 500
  margin: 0 0 20px

.reviews__text
  font-size: 14px
  line-height: 200%
  margin: 0 0 30px
</style>
