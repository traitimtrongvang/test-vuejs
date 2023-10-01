<script>
import ItemContainer from "@/components/ItemContainer.vue";

export default {
  name: "Test",
  components: {ItemContainer},
  data() {
    return {
      itemList: [
        {name: "xxx1"},
        {name: "xxx2"},
        {name: "xxx3"},
        {name: "xxx4"},
        {name: "xxx5"},
      ]
    }
  }
}
</script>

<template>
  <div class="flex flex-col items-center justify-center w-screen h-screen">
    <ItemContainer :itemList="itemList" />
    <p>{{itemList}}</p>
  </div>
</template>

<style scoped>

</style>