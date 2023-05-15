<template>
    <div v-if="!results" class="flex flex-col space-y-4 gap-4">
        <form @submit="calculateHandicap" class="flex flex-col gap-2">
            <input v-model="handicapIndex" type="text" placeholder="Handicap Index" class="w-full p-2 border border-gray-300 rounded outline-none" />
            <input v-model="slopeRating" type="text" placeholder="Slope Rating" class="w-full p-2 border border-gray-300 rounded outline-none" />
            <button type="submit" class="bg-gradient-to-r from-emerald-400 to-cyan-400 px-6 py-2 rounded w-full text-white">
                Calculate
            </button>
        </form>
    </div>
    <Results 
     v-else
     @newCalc="newCalc"
     :coursehandicap="coursehandicap" 
     />
</template>

<script setup lang="ts">
import Results from './Results.vue'
import { ref } from 'vue'

const handicapIndex = ref<any>("");
const slopeRating = ref<any>("");
const coursehandicap = ref(0);

const results = ref(false);

const calculateHandicap = (event: Event) => {
    event.preventDefault();
    const handicap = slopeRating.value / 113 * handicapIndex.value;
    coursehandicap.value = Math.round(handicap);
    results.value = true;
}

const newCalc = () => {
    results.value = false;  
    handicapIndex.value = "";
    slopeRating.value = "";
}
</script>