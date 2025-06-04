<script setup>
import logo from '@/assets/img/logo.png'; // @ is shorthand for /src
</script>

<template>
  <nav class="border-b" style="background-color: #0A2463; border-color: #3E92CC;">
    <div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
      <div class="flex h-20 items-center justify-between">
        <div class="flex flex-1 items-center justify-center md:items-stretch md:justify-start">
          <!-- Logo -->
          <a class="flex flex-shrink-0 items-center mr-4" href="index.html">
            <img class="h-10 w-auto" :src="logo" alt="Vue Jobs" />
            <span class="hidden md:block text-white text-2xl font-bold ml-2">Hirely | Vue Jobs</span>
          </a>

          <!-- Nav Links -->
          <div class="md:ml-auto">
            <div class="flex space-x-2">
              <a
                href="index.html"
                class="text-white bg-[#3E92CC] hover:bg-[#FFD700] hover:text-[#0A2463] rounded-md px-3 py-2 transition-colors duration-200"
              >Home</a>
              <a
                href="jobs.html"
                class="text-white hover:bg-[#3E92CC] hover:text-white rounded-md px-3 py-2 transition-colors duration-200"
              >Jobs</a>
              <a
                href="add-job.html"
                class="text-white hover:bg-[#3E92CC] hover:text-white rounded-md px-3 py-2 transition-colors duration-200"
              >Add Job</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>
