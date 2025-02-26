<script setup>
import { ref } from 'vue'

const leaderboard = ref([
  { rank: 1, name: '张三', points: 1200 },
  { rank: 2, name: '李四', points: 1100 },
  { rank: 3, name: '王五', points: 1000 },
  // 可以添加更多用户
])
</script>

<template>
  <div class="bg-white rounded-lg shadow-md p-4">
    <h2 class="text-xl font-bold mb-4">积分排行榜</h2>
    <div class="space-y-2">
      <div v-for="user in leaderboard" :key="user.rank"
        class="flex items-center justify-between p-3 hover:bg-gray-50 rounded-lg">
        <div class="flex items-center gap-3">
          <span class="font-bold" :class="{
            'text-yellow-500': user.rank === 1,
            'text-gray-400': user.rank === 2,
            'text-amber-600': user.rank === 3
          }">{{ user.rank }}</span>
          <span>{{ user.name }}</span>
        </div>
        <span class="text-blue-600 font-semibold">{{ user.points }}分</span>
      </div>
    </div>
  </div>
</template>
