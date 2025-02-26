<template>
  <div class="min-h-screen bg-gray-50">
    <!-- 引入全局Header组件 -->
    <Header />

    <!-- 主要内容区域 - 添加pt-16确保不被header遮挡 -->
    <div class="pt-16">
      <!-- 分类导航区域 -->
      <div class="sticky top-16 z-10 bg-white shadow-sm">
        <div class="max-w-7xl mx-auto px-4">
          <!-- 一级分类 -->
          <div class="flex overflow-x-auto py-3 scrollbar-hide">
            <div
              v-for="(category, index) in primaryCategories"
              :key="index"
              :class="[
                'px-4 py-2 mr-3 rounded-full cursor-pointer whitespace-nowrap transition-colors',
                currentPrimary === index
                  ? 'bg-gray-800 text-white'
                  : 'bg-gray-100 hover:bg-gray-200'
              ]"
              @click="selectPrimaryCategory(index)"
            >
              {{ category.name }}
            </div>
          </div>

          <!-- 二级分类 -->
          <div class="flex overflow-x-auto pb-3 scrollbar-hide">
            <div
              v-for="(subCategory, index) in currentSubCategories"
              :key="index"
              :class="[
                'px-4 py-2 mr-3 rounded-full cursor-pointer whitespace-nowrap transition-colors',
                currentSecondary === index
                  ? 'bg-gray-800 text-white'
                  : 'bg-gray-100 hover:bg-gray-200'
              ]"
              @click="selectSecondaryCategory(index)"
            >
              {{ subCategory }}
            </div>
          </div>
        </div>
      </div>

      <!-- 活动卡片展示区域 -->
      <div class="max-w-7xl mx-auto px-4 py-6">
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6">
          <div
            v-for="(activity, index) in activities"
            :key="index"
            class="bg-white rounded-lg overflow-hidden cursor-pointer transform transition-all duration-200 hover:-translate-y-1 hover:shadow-lg"
            @click="goToDetail(activity.id)"
          >
            <img
              :src="activity.image"
              :alt="activity.title"
              class="w-full h-48 object-cover"
            >
            <div class="p-4">
              <h3 class="text-lg font-medium mb-2 line-clamp-2">{{ activity.title }}</h3>
              <p class="text-sm text-gray-600 mb-1 flex items-center">
                <span class="i-carbon-time mr-1" />
                {{ activity.time }}
              </p>
              <p class="text-sm text-gray-600 flex items-center">
                <span class="i-carbon-location mr-1" />
                {{ activity.location }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import { useRouter } from 'vue-router'
import Header from '../components/header.vue'

const router = useRouter()

// 一级分类数据
const primaryCategories = ref([
  { name: '全部活动', subCategories: ['所有'] },
  { name: '艺术展览', subCategories: ['画展', '雕塑展', '装置艺术'] },
  { name: '音乐会', subCategories: ['古典音乐', '流行音乐', '爵士乐'] },
  { name: '讲座论坛', subCategories: ['文学', '科技', '艺术', '历史'] },
  { name: '戏剧表演', subCategories: ['话剧', '音乐剧', '儿童剧'] },
  { name: '电影放映', subCategories: ['主题展映', '首映会', '影展'] }
])

// 当前选中的分类
const currentPrimary = ref(0)
const currentSecondary = ref(0)

// 计算当前二级分类
const currentSubCategories = computed(() => {
  return primaryCategories.value[currentPrimary.value].subCategories
})

// 模拟活动数据
const activities = ref([
  {
    id: 1,
    title: '2024春季艺术展：当代艺术的新视界',
    image: '/images/art-exhibition.jpg',
    time: '2024-04-01 ~ 2024-04-30',
    location: '市民文化中心'
  },
  {
    id: 2,
    title: '维也纳交响乐团新年音乐会',
    image: '/images/concert.jpg',
    time: '2024-01-01 19:30',
    location: '音乐厅大剧院'
  },
  {
    id: 3,
    title: '科技创新论坛：AI与未来生活',
    image: '/images/forum.jpg',
    time: '2024-03-15 14:00',
    location: '科技会展中心'
  },
  {
    id: 4,
    title: '莎士比亚经典话剧《哈姆雷特》',
    image: '/images/theatre.jpg',
    time: '2024-02-14 ~ 2024-02-16',
    location: '大剧院主演艺厅'
  },
  {
    id: 5,
    title: '当代水墨画展：传统与现代的对话',
    image: '/images/ink-painting.jpg',
    time: '2024-05-01 ~ 2024-05-15',
    location: '现代艺术馆'
  },
  {
    id: 6,
    title: '爵士音乐节：蓝调之夜',
    image: '/images/jazz.jpg',
    time: '2024-06-20 20:00',
    location: '露天音乐广场'
  },
  {
    id: 7,
    title: '儿童艺术节：童话剧展演',
    image: '/images/children-theatre.jpg',
    time: '2024-06-01 ~ 2024-06-03',
    location: '青少年活动中心'
  },
  {
    id: 8,
    title: '国际电影展：世界电影周',
    image: '/images/film-festival.jpg',
    time: '2024-07-01 ~ 2024-07-07',
    location: '环球影城'
  }
])

// 分类选择方法
const selectPrimaryCategory = (index) => {
  currentPrimary.value = index
  currentSecondary.value = 0
}

const selectSecondaryCategory = (index) => {
  currentSecondary.value = index
}

// 跳转到详情页
const goToDetail = (id) => {
  router.push(`/detail/${id}`)
}
</script>

<style>
.scrollbar-hide {
  -ms-overflow-style: none;
  scrollbar-width: none;
}
.scrollbar-hide::-webkit-scrollbar {
  display: none;
}
</style>
