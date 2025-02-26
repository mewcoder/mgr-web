<script setup>
import Header from '../components/header.vue'
import ActivityCarousel from '../components/ActivityCarousel.vue'
import PointsLeaderboard from '../components/PointsLeaderboard.vue'
import BookStats from '../components/BookStats.vue'
</script>

<template>
  <div class="min-h-screen bg-gray-100">
    <Header />
    <main class="container mx-auto px-4 pt-20">
      <div class="lg:flex lg:gap-6">
        <!-- 左侧主要内容区 -->
        <div class="flex-1">
          <div class="space-y-6">
            <!-- 活动轮播图 -->
            <ActivityCarousel />

            <!-- 图书统计 -->
            <BookStats />
          </div>
        </div>

        <!-- 右侧积分排行榜 -->
        <div class="mt-6 lg:mt-0 lg:w-72 lg:h-[calc(100vh-6rem)] lg:sticky lg:top-24">
          <PointsLeaderboard class="h-full" />
        </div>
      </div>
    </main>
  </div>
</template>
