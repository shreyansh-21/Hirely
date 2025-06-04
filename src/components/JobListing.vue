<script setup>
import { defineProps } from 'vue';
defineProps({
  job: Object
});
</script>

<template>
  <div class="bg-white rounded-xl shadow-md relative border border-[#E5E7EB]">
    <div class="p-4">
      <div class="text-[#3E92CC] my-2 font-medium">{{ job.type }}</div>
      <h3 class="text-xl font-bold text-[#0A2463]">{{ job.title }}</h3>
      <div class="mb-5 text-[#333]">{{ job.description }}</div>
      <h3 class="text-[#FFD700] mb-2 font-semibold">{{ job.salary }} /year</h3>
      <div class="text-[#0A2463] mb-3">
        <i class="fa-solid fa-location-dot text-lg mr-1"></i>
        {{ job.location }}
      </div>
    </div>

    <div class="bg-[#F8FAFC] border-t border-[#E2E8F0] p-4">
      <div class="flex flex-col lg:flex-row justify-between items-center">
        <h3 class="text-[#0A2463] mb-3 font-bold">NewTek Solutions</h3>
        <a
          :href="'/job/' + job.id"
          class="h-[40px] bg-[#3E92CC] hover:bg-[#FFD700] hover:text-[#0A2463] text-white px-4 py-2 rounded-md text-xs font-bold uppercase text-center transition-colors duration-200"
        >
          Read More
        </a>
      </div>
    </div>
  </div>
</template>
