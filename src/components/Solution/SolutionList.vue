<template>
  <v-container>
    <v-card class="text-left">
      <v-card-title>Solutions</v-card-title>
      <v-container>
        <v-list>
          <SolutionListItem
              v-for="item in solutions"
              :key="item.path"
              :solution="item"
              @click="$emit('click', item)"
          ></SolutionListItem>
        </v-list>
      </v-container>

    </v-card>
  </v-container>
</template>
<script>
import SolutionListItem from "@/components/Solution/SolutionListItem";

export default {
  name: "SolutionList",
  components: {SolutionListItem},
  props: {
    controller: {
      type: Object,
      required: true
    },
    solutions: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>

</style>