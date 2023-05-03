<template>
    <div class="grid md:grid-cols-2 gap-4">
        <div class="shadow-md bg-blue-100 p-10 text-center rounded">
            <h3 class="text-3xl text-blue-900 font-bold mb-4">
                Cases
            </h3>

            <div class="text-2xl mb4">
                <span class="font-bold">New:</span>
                {{ numberWithCommas(stats.NewConfirmed) }}
            </div>
            <div class="text-2xl mb4">
                <span class="font-bold">Total:</span>
                {{ numberWithCommas(stats.TotalConfirmed) }}
            </div>
        </div>
        <div class="shadow-md bg-red-100 p-10 text-center rounded">
            <h3 class="text-3xl text-blue-900 font-bold mb-4">
                Deaths
            </h3>

            <div class="text-2xl mb4">
                <span class="font-bold">New:</span>
                {{ numberWithCommas(stats.NewDeaths) }}
            </div>
            <div class="text-2xl mb4">
                <span class="font-bold">Total:</span>
                {{ numberWithCommas(stats.TotalDeaths) }}
            </div>
        </div>
    </div>
</template>
  
<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: "DataBoxes",
    props: ['stats'],
    setup() {

        return {
            numberWithCommas(x : string) {
                return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
            },
        }
    },
});
</script>
  