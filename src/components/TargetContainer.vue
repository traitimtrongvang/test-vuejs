<script>
import Target from "@/components/Target.vue";

export default {
  name: "TargetContainer",
  components: {Target},
  props: {
    targetList: Array,
    isAddNewFormPerform: Boolean
  },

  methods: {
    handleDeleteTarget(index) {
      this.targetList.splice(index, 1)
    }
  }
}
</script>

<template>
  <section>

    <p>Muc Tieu Ca Nhan</p>

    <section>
      <Target
          v-for="(target, index) in targetList"
          v-model="target.content"
          :index="index+1"
          :stepList="target.stepList"
          :onClickDelete="() => handleDeleteTarget(index)"
      />
    </section>

  </section>
</template>

<style scoped>

</style>