<script>
import ItemContainer from "@/components/ItemContainer.vue";

export default {
  name: "Target",
  components: {ItemContainer},

  props: {
    index: Number,
    stepList: Array,
    modelValue: String,
    onClickDelete: Function
  }
}
</script>

<template>
  <article class="grid grid-cols-[1fr_1.3fr]">

    <section>
      <h3>Muc Tieu {{index}}</h3>
      <textarea
          :value="modelValue"
          @input="$emit('update:modelValue', $event.target.value)"
          class="w-full border-[1px] border-gray-400"></textarea>
      <button @click="onClickDelete" class="bg-red-400">Xoa Muc tiu</button>
    </section>

    <section>
      <ItemContainer :itemList="stepList" title="Cac buoc Tien hanh"/>
    </section>

  </article>
</template>

<style scoped>

</style>