<template>
  <header class="text-center bg-blue-800 text-white p-4 mb-10">
    <div class="text-3xl md:text-5xl font-bold mb-3">
      <!-- **@issue: icon not showing -->
      <i class="fab fa-viruses"></i>
      Covid-19 Tracker
    </div>

    <p>API by <a class="text-blue-300" href="https://covid19api.com" target="_blank">https://covid19api.com</a></p>
  </header>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';

  export default defineComponent({
    name: 'Header',
  });
</script>


