<!-- This example requires Tailwind CSS v2.0+ -->
<template>
  <div class="relative overflow-hidden bg-white">
    <div class="mx-auto max-w-7xl">
      <div class="relative z-10 pb-8 bg-white sm:pb-16 md:pb-20 lg:max-w-2xl lg:w-full lg:pb-28 xl:pb-32">
        <svg class="absolute inset-y-0 right-0 hidden w-48 h-full text-white transform translate-x-1/2 lg:block" fill="currentColor" viewBox="0 0 100 100" preserveAspectRatio="none" aria-hidden="true">
          <polygon points="50,0 100,0 50,100 0,100" />
        </svg>

        <TheHeader />

        <main class="px-4 mx-auto mt-10 max-w-7xl sm:mt-12 sm:px-6 md:mt-16 lg:mt-20 lg:px-8 xl:mt-28">
          <div class="sm:text-center lg:text-left">
            <h1 class="text-4xl font-extrabold tracking-tight text-gray-900 sm:text-5xl md:text-6xl">
              <span class="block xl:inline">All Your imgix Demos</span>
              {{ ' ' }}
              <span class="block text-5xl text-orange-600 xl:inline">Three Powerful Languages</span>
            </h1>
            <p class="mt-3 text-base text-gray-500 sm:mt-5 sm:text-lg sm:max-w-xl sm:mx-auto md:mt-5 md:text-xl lg:mx-0">imgix transforms, optimizes, and intelligently caches your entire asset library for faster pages, higher engagement, and a simpler workflow.</p>
            <div class="mt-5 sm:mt-8 sm:flex sm:justify-center lg:justify-start">
              <div class="rounded-md shadow">
                <a href="https://dashboard.imgix.com/sign-up" class="flex items-center justify-center w-full px-8 py-3 text-base font-medium text-white bg-orange-600 border border-transparent rounded-md hover:bg-indigo-700 md:py-4 md:text-lg md:px-10"> TRY IT FREE </a>
              </div>
              <div class="mt-3 sm:mt-0 sm:ml-3">
                <a href="#" class="flex items-center justify-center w-full px-8 py-3 text-base font-medium text-indigo-700 bg-indigo-100 border border-transparent rounded-md hover:bg-indigo-200 md:py-4 md:text-lg md:px-10"> See Demos </a>
              </div>
            </div>
          </div>
        </main>
         
      </div>
    </div>
    <div class="lg:absolute lg:inset-y-0 lg:right-0 lg:w-1/2">
      <img class="object-cover w-full h-56 sm:h-72 md:h-96 lg:w-full lg:h-full" src="https://ix-www.imgix.net/press/imgix-unsplash.jpeg?w=1200&auto=format,compress&cs=srgb" alt="" />
    </div>
  </div>
  <!-- Sections -->
  <div class="relative px-4 pt-16 pb-20 bg-gray-50 sm:px-6 lg:pt-24 lg:pb-28 lg:px-8">
    <div class="absolute inset-0">
      <div class="bg-white h-1/3 sm:h-2/3" />
    </div>
    <div class="relative mx-auto max-w-7xl">
      <div class="text-center">
        <h2 class="text-3xl font-extrabold tracking-tight text-gray-900 sm:text-4xl">imgix Demos</h2>
        <p class="max-w-2xl mx-auto mt-3 text-xl text-gray-500 sm:mt-4">These are a list of some demos we have made using imgix Video, Vue, React, and Javascript.</p>
      </div>
      <div class="grid gap-16 mt-12 lg:grid-cols-3 lg:gap-x-5 lg:gap-y-12">
        <div
          v-for="article in qc"
          :key="article._path"
          class="flex flex-col justify-between p-4 border border-gray-200 rounded-lg"
        >
          <nuxt-link :href="article._path">
            <p class="text-xl text-gray-900">{{ article.title }}</p>
            <p class="mt-3 text-gray-500">{{ article.description }}</p>
          </nuxt-link>
          
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
  import { Popover, PopoverButton, PopoverPanel } from '@headlessui/vue'
  import { MenuIcon, XIcon } from '@heroicons/vue/outline'

const { query } = useRoute();
const { author } = query;

const qc = await queryContent("demo")
  .where({ author })
  .sort({ _file: -1, $numeric: true })
  .find();


  </script>