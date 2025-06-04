<script setup>
import { defineProps } from 'vue';

defineProps({
  title: {
    type: String,
    default: 'Become a Vue Dev',
  },
  subtitle: {
    type: String,
    default: 'Find the Vue job that fits your skills and needs',
  },
});
</script>

<template>
  <section class="py-20 mb-4" style="background-color: #0A2463;">
    <div
      class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col items-center"
    >
      <div class="text-center">
        <h1
          class="text-4xl font-extrabold sm:text-5xl md:text-6xl"
          style="color: #FFFFFF;"
        >
          {{ title }}
        </h1>
        <p class="my-4 text-xl" style="color: #FFD700;">
          {{ subtitle }}
        </p>
      </div>
    </div>
  </section>
</template>
