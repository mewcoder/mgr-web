<script setup>
import { ref } from 'vue'

const stats = ref({
  total: 5000,
  borrowed: 1200,
  available: 3800
})
</script>

<template>
  <div class="bg-white rounded-lg shadow-md p-6">
    <h2 class="text-xl font-bold mb-6">图书统计</h2>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
      <div class="flex flex-col items-center p-6 bg-blue-50 rounded-lg">
        <span class="text-gray-600 mb-2">总藏书量</span>
        <span class="text-3xl font-bold text-blue-600">{{ stats.total }}</span>
      </div>
      <div class="flex flex-col items-center p-6 bg-green-50 rounded-lg">
        <span class="text-gray-600 mb-2">可借数量</span>
        <span class="text-3xl font-bold text-green-600">{{ stats.available }}</span>
      </div>
      <div class="flex flex-col items-center p-6 bg-orange-50 rounded-lg">
        <span class="text-gray-600 mb-2">借出数量</span>
        <span class="text-3xl font-bold text-orange-600">{{ stats.borrowed }}</span>
      </div>
    </div>
  </div>
</template>
