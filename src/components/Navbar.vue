<script setup>
import { RouterLink, useRoute } from 'vue-router';
import logo from '@/assets/img/logo.png';

const isActiveLink = (routePath) => {
  const route = useRoute();
  return route.path === routePath;
};
</script>

<template>
  <nav class="bg-[#0A2463] border-b border-[#3E92CC] shadow-md">
    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
      <div class="flex h-20 items-center justify-between">
        <!-- Left Side: Logo and Title -->
        <div class="flex items-center space-x-4">
          <RouterLink class="flex items-center" to="/">
            <img class="h-10 w-auto" :src="logo" alt="Vue Jobs" />
            <span class="hidden md:block text-white text-2xl font-semibold ml-2 tracking-wide">
              Vue Jobs
            </span>
          </RouterLink>
        </div>

        <!-- Right Side: Nav Links -->
        <div class="flex space-x-3">
          <RouterLink
            to="/"
            :class="[
              isActiveLink('/') ? 'bg-[#FFD700] text-[#0A2463]' : 'text-white hover:bg-[#3E92CC]',
              'px-4 py-2 rounded-md text-sm font-medium transition-colors duration-200'
            ]"
          >
            Home
          </RouterLink>
          <RouterLink
            to="/jobs"
            :class="[
              isActiveLink('/jobs') ? 'bg-[#FFD700] text-[#0A2463]' : 'text-white hover:bg-[#3E92CC]',
              'px-4 py-2 rounded-md text-sm font-medium transition-colors duration-200'
            ]"
          >
            Jobs
          </RouterLink>
          <RouterLink
            to="/jobs/add"
            :class="[
              isActiveLink('/jobs/add') ? 'bg-[#FFD700] text-[#0A2463]' : 'text-white hover:bg-[#3E92CC]',
              'px-4 py-2 rounded-md text-sm font-medium transition-colors duration-200'
            ]"
          >
            Add Job
          </RouterLink>
        </div>
      </div>
    </div>
  </nav>
</template>
