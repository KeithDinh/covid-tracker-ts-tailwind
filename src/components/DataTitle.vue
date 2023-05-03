<template>
  <div class="text-center">
    <h2 class="text-3xl font-bold">{{ text }}</h2>
    <div class="text-2xl mt-4 mb-10">
      {{ timestamp }}
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, defineProps, computed } from "vue";
import moment from 'moment'

export default defineComponent({
  name: "DataTitle",
  props: ['text', 'dataDate'],
  setup({dataDate}) {
    return {
        timestamp: computed(() => moment(dataDate)
        .format('MMMM Do YYYY, h:mm:ss a'))
    }
  },
});
</script>
