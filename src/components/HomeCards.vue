<script setup>
import Card from '@/components/Card.vue';
</script>

<template>
  <section class="py-4" style="background-color: #FFFFFF;">
    <div class="container-xl lg:container m-auto">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-4 p-4 rounded-lg">
        <!-- Developer Card -->
        <Card :bg="'bg-white'">
          <h2 class="text-2xl font-bold text-[#0A2463]">For Developers</h2>
          <p class="mt-2 mb-4 text-[#0A2463]">
            Browse our Vue jobs and start your career today
          </p>
          <a
            href="jobs.html"
            class="inline-block bg-[#3E92CC] text-white rounded-lg px-4 py-2 hover:bg-[#FFD700] hover:text-[#0A2463] transition-colors duration-200"
          >
            Browse Jobs
          </a>
        </Card>

        <!-- Employer Card -->
        <Card :bg="'bg-blue-50'">
          <h2 class="text-2xl font-bold text-[#0A2463]">For Employers</h2>
          <p class="mt-2 mb-4 text-[#0A2463]">
            List your job to find the perfect developer for the role
          </p>
          <a
            href="add-job.html"
            class="inline-block bg-[#3E92CC] text-white rounded-lg px-4 py-2 hover:bg-[#FFD700] hover:text-[#0A2463] transition-colors duration-200"
          >
            Add Job
          </a>
        </Card>
      </div>
    </div>
  </section>
</template>
