<script>
import Item from "@/components/Item.vue";

export default {
  name: "ItemContainer",

  components: {Item},

  props: {
    title: String,
    itemList: Array,
    class: String
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
      this.itemList.splice(ind, 1)
    },

    handleCompleteAddNewItem(newName) {
      if (newName) this.itemList.push({name: newName})
      this.isAddNew = false
    }

  }
}
</script>

<template>
  <section class="flex flex-col gap-3 w-[300px] {{this.class}}">

    <p>{{title}}</p>

    <Item
        v-for="(item, ind) in itemList"
        v-model="item.name"
        :key="ind"
        :onClose="() => handleRemoveItem(ind)"
    />

    <Item
        v-if="isAddNew"
        :isFocus="true"
        :onSave="handleCompleteAddNewItem"
    />

    <button @click="handleTriggerAddNewItem">add new</button>

  </section>
</template>