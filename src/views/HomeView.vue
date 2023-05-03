<template>
  <main v-if="!loading">
    <DataTitle :text="title" :dataDate="dataDate" />
    
    <DataBoxes :stats="stats" />

    <CountrySelect @get-country="getCountryData" :countries="countries" />

    <button
      @click="clearCountryData"
      v-if="stats.Country"
      class="bg-green-700 text-white rounded p-3 mt-10 focus:outline-none hover:bg-green-600"
    >
      Clear Country
    </button>
  </main>

  <main v-else class="flex flex-col align-center justify-center text-center">
    <div class="text-gray-500 text-3xl mt-10 mb-6">
      Fetching Data
    </div>
    <img class="w-24 m-auto" src="../assets/hourglass.gif" alt="">
  </main>
</template>

<script lang="ts">
import { defineComponent, onBeforeMount, ref } from 'vue';
import DataTitle from '@/components/DataTitle.vue';
import DataBoxes from '@/components/DataBoxes.vue';
import CountrySelect from '@/components/CountrySelect.vue';

export default defineComponent({
  name: 'HomeView',
  components: {
    DataTitle,
    DataBoxes,
    CountrySelect
  },
  setup() {
    const loading = ref(true);
    const title = ref('Global');
    const dataDate = ref('');
    const stats = ref({});
    const countries = ref([]);

    async function fetchCovidData() {
      const res = await fetch('https://api.covid19api.com/summary')
      const data = await res.json()
      return data
    }
    
    // **@issue: need to correct the type of country
    const getCountryData = (country:any) => {
      stats.value = country;
      title.value = country.Country;
    };

    const clearCountryData = async () => {
      loading.value = true;
      const data = await fetchCovidData();
      title.value = 'Global';
      stats.value = data.Global;
      loading.value = false;
    };

    onBeforeMount(async () => {
      const data = await fetchCovidData()

      dataDate.value = data?.Date
      stats.value = data?.Global
      countries.value = data?.Countries
      
      loading.value = false;
    })

    return {
      loading,
      title,
      dataDate,
      stats,
      countries,
      getCountryData,
      clearCountryData
    }
  },
})
</script>


