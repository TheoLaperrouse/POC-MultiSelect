<template>
  <div>
    <h3 class="title">{{ title }}</h3>
    <Multiselect v-model="value" :options="options" :mode="mode"></Multiselect>
    <span>{{ value }}</span>
  </div>
</template>

<script>
import Multiselect from '@vueform/multiselect'

export default {
  components: {
    Multiselect
  },
  props: {
    title: {
      type: String
    },
    mode: { type: String },
    options: {
      type: Array,
      default: () => []
    }
  },
  data() {
    return {
      value: null
    }
  }
}
</script>

<style src="@vueform/multiselect/themes/default.css">
.title {
  font-weight: 900;
}
</style>
