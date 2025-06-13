<script setup>
import PulseLoader from 'vue-spinner/src/PulseLoader.vue';
import BackButton from '@/components/BackButton.vue';
import { reactive, onMounted } from 'vue';
import { useRoute, RouterLink, useRouter } from 'vue-router';
import { useToast } from 'vue-toastification';
import axios from 'axios';

const route = useRoute();
const router = useRouter();
const toast = useToast();

const jobId = route.params.id;

const state = reactive({
  job: {},
  isLoading: true,
});

const deleteJob = async () => {
  try {
    const confirm = window.confirm('Are you sure you want to delete this job?');
    if (confirm) {
      await axios.delete(`/api/jobs/${jobId}`);
      toast.success('Job Deleted Successfully');
      router.push('/jobs');
    }
  } catch (error) {
    console.error('Error deleting job', error);
    toast.error('Job Not Deleted');
  }
};

onMounted(async () => {
  try {
    // const response = await axios.get(`/api/jobs/${jobId}`);
    const response = await axios.get(`/api/jobs/${jobId}`);
    state.job = response.data;
  } catch (error) {
    console.error('Error fetching job', error);
  } finally {
    state.isLoading = false;
  }
});
</script>

<template>
  <BackButton />
  <section v-if="!state.isLoading" class="bg-[#f9fbfd] min-h-screen">
    <div class="container m-auto py-10 px-6">
      <div class="grid grid-cols-1 md:grid-cols-[70%_30%] gap-6">
        <!-- Main Job Info -->
        <main>
          <div class="bg-white p-6 rounded-lg shadow text-center md:text-left">
            <div class="text-[#3E92CC] mb-2 uppercase tracking-wide font-medium">
              {{ state.job.type }}
            </div>
            <h1 class="text-3xl font-bold mb-4 text-[#0A2463]">
              {{ state.job.title }}
            </h1>
            <div class="text-[#3E92CC] flex items-center justify-center md:justify-start mb-4">
              <i class="pi pi-map-marker text-xl mr-2"></i>
              <p>{{ state.job.location }}</p>
            </div>
          </div>

          <div class="bg-white p-6 rounded-lg shadow mt-6">
            <h3 class="text-[#0A2463] text-lg font-semibold mb-4">Job Description</h3>
            <p class="mb-6 text-gray-700 leading-relaxed">
              {{ state.job.description }}
            </p>

            <h3 class="text-[#0A2463] text-lg font-semibold mb-2">Salary</h3>
            <p class="text-[#3E92CC] font-semibold text-xl">
              ₹{{ state.job.salary }} / Year
            </p>
          </div>
        </main>

        <!-- Sidebar -->
        <aside>
          <!-- Company Info -->
          <div class="bg-white p-6 rounded-lg shadow">
            <h3 class="text-xl font-bold mb-4 text-[#0A2463]">Company Info</h3>
            <h2 class="text-2xl text-[#3E92CC]">{{ state.job.company.name }}</h2>
            <p class="my-3 text-gray-600">{{ state.job.company.description }}</p>

            <hr class="my-4 border-[#3E92CC]" />

            <div>
              <h4 class="text-md font-semibold text-[#0A2463]">Contact Email:</h4>
              <p class="bg-[#f0f8ff] p-2 rounded mt-1 text-[#0A2463] font-medium">
                {{ state.job.company.contactEmail }}
              </p>

              <h4 class="text-md font-semibold mt-4 text-[#0A2463]">Contact Phone:</h4>
              <p class="bg-[#f0f8ff] p-2 rounded mt-1 text-[#0A2463] font-medium">
                {{ state.job.company.contactPhone }}
              </p>
            </div>
          </div>

          <!-- Manage Job -->
          <div class="bg-white p-6 rounded-lg shadow mt-6">
            <h3 class="text-xl font-bold mb-4 text-[#0A2463]">Manage Job</h3>

            <RouterLink
              :to="`/jobs/edit/${state.job.id}`"
              class="block w-full text-center bg-[#3E92CC] hover:bg-[#2f7bb4] text-white font-bold py-2 px-4 rounded-full mt-2 transition-all"
            >
              Edit Job
            </RouterLink>

            <button
              @click="deleteJob"
              class="block w-full bg-red-500 hover:bg-red-600 text-white font-bold py-2 px-4 rounded-full mt-4 transition-all"
            >
              Delete Job
            </button>
          </div>
        </aside>
      </div>
    </div>
  </section>

  <!-- Loader -->
  <div v-else class="text-center text-[#3E92CC] py-6">
    <PulseLoader :loading="true" color="#0A2463" />
  </div>
</template>
