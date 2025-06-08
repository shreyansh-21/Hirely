<script setup>
import { defineProps, ref, computed } from 'vue';

const props = defineProps({
  job: Object
});

const showFullDescription = ref(false);

const truncatedDescription = computed(() => {
  if (!props.job?.description) return '';
  
  const description = props.job.description;
  
  if (showFullDescription.value) {
    return description;
  }
  
  return description.length > 100 ? description.slice(0, 90) + '...' : description;
});
</script>

<template>
  <div class="bg-white rounded-xl shadow-md relative border border-[#E5E7EB]">
    <div class="p-4">
      <div class="text-[#3E92CC] my-2 font-medium">{{ props.job.type }}</div>
      <h3 class="text-xl font-bold text-[#0A2463]">{{ props.job.title }}</h3>
      <div class="mb-5 text-[#333]">
        {{ truncatedDescription }}
        <button 
          v-if="props.job.description && props.job.description.length > 100"
          @click="showFullDescription = !showFullDescription"
          class="text-[#3E92CC] hover:underline ml-1"
        >
          {{ showFullDescription ? 'Show less' : 'Show more' }}
        </button>
      </div>
      <h3 class="text-[#FFD700] mb-2 font-semibold">{{ props.job.salary }} /year</h3>
      <div class="text-[#0A2463] mb-3">
        <i class="pi pi-map-marker"></i>
        {{ props.job.location }}
      </div>
    </div>

    <div class="bg-[#F8FAFC] border-t border-[#E2E8F0] p-4">
      <div class="flex flex-col lg:flex-row justify-between items-center">
        <h3 class="text-[#0A2463] mb-3 font-bold">NewTek Solutions</h3>
        <RouterLink
          :to="'/jobs/' + props.job.id"
          class="h-[40px] bg-[#3E92CC] hover:bg-[#FFD700] hover:text-[#0A2463] text-white px-4 py-2 rounded-md text-xs font-bold uppercase text-center transition-colors duration-200"
        >
          Read More
        </RouterLink>
      </div>
    </div>
  </div>
</template>