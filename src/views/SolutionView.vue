<template>
  <v-container>
    <SolutionListGetter :controller="controller">
      <template v-slot="{solutions, reload}">
        <SolutionList :controller="controller" :solutions="solutions" @updated="reload"></SolutionList>
      </template>
    </SolutionListGetter>
  </v-container>
</template>

<script>
import SolutionListGetter from "@/components/Solution/SolutionListGetter";
import SolutionList from "@/components/Solution/SolutionList";
export default {
  name: "SolutionView",
  components: {SolutionList, SolutionListGetter},
  props: {
    controller: {
      type: Object,
      required: true
    }
  },
}
</script>

<style scoped>

</style>