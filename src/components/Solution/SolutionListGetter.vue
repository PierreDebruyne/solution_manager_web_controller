<template>
  <div>
    <slot v-if="status === 'loading'" name="loading">
      <div>Loading...</div>
    </slot>
    <slot v-else-if="status === 'success'" :solutions="solutions" :reload="do_request"></slot>
    <slot v-else-if="status === 'error'">
      Error
    </slot>
  </div>
</template>

<script>
export default {
  name: "SolutionListGetter",
  props: {
    controller: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      status: 'loading',
      solutions: null
    }
  },
  methods: {
    async do_request() {
      try {
        this.solutions = await this.controller.get_solutions();
        this.status = "success";
      } catch (e) {
        console.log(e)
        this.status = "error";
      }
    }
  },
  mounted() {
      this.do_request();
  }
}
</script>

<style scoped>

</style>