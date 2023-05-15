<template>
      <div class="flex flex-col space-y-4 gap-4 text-center">
        <p class="text-2xl font-bold">Your Course Handicap is:</p>
        <p class="text-4xl font-bold">{{ coursehandicap }}</p>
        <button class="bg-gradient-to-r from-emerald-400 to-cyan-400 px-6 py-2 rounded w-full text-white" text="Calculate Another Handicap" @click="emit('newCalc')">
            Calculate Another Handicap
        </button>
    </div>
</template>

<script setup lang="ts">
const props = defineProps({
  coursehandicap: {
    type: Number,
    required: true
  }
})

const emit = defineEmits(['newCalc'])

</script>