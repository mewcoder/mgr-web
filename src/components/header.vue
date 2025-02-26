<script setup>
import { ref } from 'vue'

const menuItems = ref([
  { name: '首页', link: '/' },
  { name: '活动', link: '/products' },
  { name: '图书', link: '/services' },
  { name: '积分商城', link: '/about' },
])
</script>

<template>
  <header class="fixed w-full top-0 z-50">
    <div class="container mx-auto p-4">
      <div class="flex items-center justify-between h-16">
        <!-- Logo -->
        <a href="#" class="flex items-start gap-2 group">
          <div class="bg-blue-600 text-white p-2 rounded-md ">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24"
              stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
            </svg>
          </div>
          <p class="text-sm font-light uppercase">
            技术平台部
            <span class="text-base block font-bold tracking-widest">
              活动管理系统
            </span>
          </p>
        </a>


        <!--  Menu -->
        <ul class="hidden md:flex space-x-4">
          <li v-for="item in menuItems" :key="item.name"><a :href="item.link"
              class="px-2 xl:px-4 py-2 text-gray-600 rounded-md hover:bg-gray-200">{{
                item.name
              }}</a></li>

        </ul>

        <div></div>

        <!-- Right Section -->
        <div class="flex items-center space-x-4">
          <a href="/contact" class="text-gray-600 hover:text-gray-900 font-medium text-sm">后台管理</a>
          <div class="h-8 w-8 rounded-full bg-gray-200 overflow-hidden">
            <img src="https://via.placeholder.com/32" alt="User avatar" class="h-full w-full object-cover">
          </div>
        </div>
      </div>
    </div>
  </header>
</template>
