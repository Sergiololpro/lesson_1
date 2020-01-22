<template>
  <div class="myInput">
    <label :for="name">
      {{ label }}
      <span v-if="isRequired">*</span>
    </label>
    <template v-if="isTextarea">
      <textarea
        :value="value"
        @input="$emit('input', $event.target.value)"
        :id="name"
        :placeholder="placeholder"
        :class="{ myInput__error: !value.length && isRequired && isValidation }"
      />
    </template>
    <template v-else>
      <input
        :value="value"
        @input="$emit('input', $event.target.value)"
        :id="name"
        :placeholder="placeholder"
        :class="{ myInput__error: !value.length && isRequired && isValidation }"
      >
    </template>
    <div class="myInput__error_text"
      v-if="!value.length && isRequired && isValidation"
      v-text="errorText"
    />
  </div>
</template>

<script>
export default {
  name: 'Input',
  props: {
    value: {
      type: String
    },
    name: {
      type: String
    },
    label: {
      type: String
    },
    placeholder: {
      type: String
    },
    errorText: {
      type: String
    },
    isTextarea: {
      type: Boolean,
      default: false
    },
    isRequired: {
      type: Boolean,
      default: false
    },
    isValidation: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="sass">
.myInput
  margin: 0 0 20px
    
label
  display: inline-block
  font-size: 14px
  position: relative
  margin: 0 0 6px
  span
    font-size: 18px
    color: #f36f6f
    font-weight: 700
    position: absolute
    right: -15px
    top: -5px

input,
textarea
  width: 100%
  border: 2px solid #322f31
  font-size: 14px
  padding: 10px 14px
  transition: border .3s ease-out

textarea
  height: 100px
  
.myInput__error
  border: 2px solid #f36f6f

.myInput__error_text
  font-size: 14px
  color: #f36f6f
  padding: 0 14px
  margin: 8px 0 0
</style>
