<script>
import Item from "@/components/Item.vue";

export default {
  name: "ItemContainer",

  components: {Item},

  props: {
    title: String,
    data: Object,
    class: String,
    error: String
  },

  watch: {
    ["data.value"]: {
      deep: true,
      handler(newVal, oldVal) {
        for (const rule of this.data.validationRuleList) {
          this.data.error = rule.behavior === "on-change" && rule.condition(newVal) ? rule.error : ""
        }
      }
    }
  },

  data() {
    return {
      isAddNew: false
    }
  },

  methods: {

    handleTriggerAddNewItem() {
      this.isAddNew = true
    },

    handleRemoveItem(ind) {
      this.data.value.splice(ind, 1)
    },

    handleCompleteAddNewItem(newVal) {
      if (newVal) this.data.value.push({error: "", value: newVal})
      this.isAddNew = false
    }

  }
}
</script>
<template>
  <section class="flex flex-col gap-3 w-[300px] {{this.class}}">

    <p>{{title}}</p>

    <Item
        v-for="(item, ind) in data.value"
        v-model="item.value"
        :error="item.error"
        :key="ind"
        :onClose="() => handleRemoveItem(ind)"
    />

    <Item
        v-if="isAddNew"
        :isFocus="true"
        :onSave="handleCompleteAddNewItem"
    />

    <p>{{data.error}}</p>

    <button @click="handleTriggerAddNewItem">add new</button>

  </section>
</template>