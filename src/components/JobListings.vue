<script setup>
import { ref , defineProps , onMounted} from 'vue'
import axios from 'axios';
import JobListing from './JobListing.vue'
import { RouterLink } from 'vue-router';
defineProps({
    limit: Number,
    showButton: {
        type: Boolean,
        default: false
    }
})
const jobs = ref([])
onMounted(async () => {
    try {
        const response = await axios.get('http://localhost:3000/jobs');
        jobs.value = response.data;
    } catch (error) {
        console.error('Error fetching jobs:', error);
    }
});
</script>

<template>
  <section class="px-4 py-10" style="background-color: #FFFFFF;">
    <div class="container-xl lg:container m-auto">
      <h2
        class="text-3xl font-bold mb-6 text-center"
        style="color: #0A2463;"
      >
        Browse Jobs
      </h2>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <JobListing
          v-for="job in jobs.slice(0, limit || jobs.length)"
          :key="job.id"
          :job="job"
        />
      </div>
    </div>
  </section>

    <section v-if="showButton"class="m-auto max-w-lg my-10 px-6">
      <RouterLink to="/jobs"
        class="block bg-[#87CEEB] text-white text-center py-4 px-6 rounded-xl hover:bg-[#FFD700]">
        View All Jobs</RouterLink>
    </section>
</template>
