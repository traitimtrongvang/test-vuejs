<script>
export default {
  name: "Item",

  props: {
    modelValue: String, // the name have to be modelValue
    onClose: Function,
    onSave: Function,
    isFocus: Boolean
  },

  mounted() {
    if (this.isFocus) {
      this.$refs.inputRef.focus()
      this.$refs.inputRef.select()
    }
  },

  data() {
    return {
      value: this.modelValue ?? "",
      inputRef: null
    }
  },

  methods: {
    handleInputChange(newValue) {
      this.value = newValue;
      this.$emit("update:modelValue", newValue)
    },
    handleInputBlur() {
      this.onSave && this.onSave(this.value)
    }
  }
}
</script>

<template>
  <article class="w-full flex">
    <input
        type="text"
        class="w-full bg-gray-200 focus:bg-white p-3"
        ref="inputRef"
        :value="modelValue"
        @input="handleInputChange($event.target.value)"
        @blur="handleInputBlur"
    >

    <button
        class="p-3"
        @click="onClose"
    >
      X
    </button>

  </article>
</template>