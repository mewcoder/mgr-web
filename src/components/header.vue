<script setup>
import { ref } from 'vue'

const menuItems = ref([
  { name: '首页', link: '/' },
  { name: '产品', link: '/products' },
  { name: '服务', link: '/services' },
  { name: '关于我们', link: '/about' },
])
</script>

<template>
  <header class="bg-white shadow-md fixed w-full top-0 z-50">
    <div class="container mx-auto px-4">
      <div class="flex items-center justify-between h-16">
        <!-- Logo -->
        <div class="flex-shrink-0">
          <h1 class="text-2xl font-bold text-gray-800">Company Name</h1>
        </div>

        <!-- Navigation Menu -->
        <nav class="hidden md:flex space-x-8">
          <a v-for="item in menuItems" :key="item.name" :href="item.link"
            class="text-gray-600 hover:text-gray-900 px-3 py-2 rounded-md text-sm font-medium transition-colors duration-200">
            {{ item.name }}
          </a>
        </nav>

        <!-- Right Section -->
        <div class="flex items-center space-x-4">
          <a href="/contact" class="text-gray-600 hover:text-gray-900 font-medium text-sm">联系我们</a>
          <div class="h-8 w-8 rounded-full bg-gray-200 overflow-hidden">
            <img src="https://via.placeholder.com/32" alt="User avatar" class="h-full w-full object-cover">
          </div>
        </div>
      </div>
    </div>
  </header>
</template>
