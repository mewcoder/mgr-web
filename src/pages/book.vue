<template>
  <div class="min-h-screen bg-gray-50">
    <Header />
    <div class="container mx-auto px-4 py-8 mt-16">
      <!-- 搜索框 -->
      <div class="mb-8">
        <div class="max-w-xl mx-auto">
          <h2 class="text-2xl font-bold text-gray-800 mb-4 text-center">图书检索</h2>
          <div class="relative">
            <input
              v-model="searchQuery"
              type="text"
              placeholder="搜索书名、作者或分类..."
              class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent"
              @input="handleSearch"
            >
            <span class="absolute right-3 top-2.5 text-gray-400">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
              </svg>
            </span>
          </div>
        </div>
      </div>

      <!-- 图书列表 -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6">
        <div
          v-for="book in filteredBooks"
          :key="book.id"
          class="bg-white rounded-lg shadow-md overflow-hidden hover:shadow-lg transition-shadow duration-300 cursor-pointer"
          @click="router.push(`/detail`)"
        >
          <img :src="book.cover" :alt="book.title" class="w-full h-48 object-cover">
          <div class="p-4">
            <div class="flex items-center gap-2 mb-2">
              <span class="px-2 py-1 bg-blue-100 text-blue-600 text-xs rounded-full">{{ book.category }}</span>
              <span v-if="book.available" class="px-2 py-1 bg-green-100 text-green-600 text-xs rounded-full">可借阅</span>
              <span v-else class="px-2 py-1 bg-red-100 text-red-600 text-xs rounded-full">已借出</span>
            </div>
            <h3 class="text-lg font-semibold text-gray-800 mb-2">{{ book.title }}</h3>
            <p class="text-sm text-gray-600 mb-2">{{ book.author }}</p>
            <div class="flex justify-between items-center">
              <span class="text-sm text-gray-500">馆藏数量: {{ book.total }}</span>
              <button
                class="px-3 py-1 bg-blue-500 text-white rounded-md hover:bg-blue-600 transition-colors duration-300"
                :disabled="!book.available"
                :class="{'opacity-50 cursor-not-allowed': !book.available}"
              >
                借阅
              </button>
            </div>
          </div>
        </div>
      </div>

      <!-- 无搜索结果提示 -->
      <div v-if="filteredBooks.length === 0" class="text-center text-gray-500 mt-8">
        未找到相关图书
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import { useRouter } from 'vue-router'
import Header from '../components/header.vue'

const router = useRouter()

// 模拟图书数据
const books = ref([
  {
    id: 1,
    title: '三体',
    author: '刘慈欣',
    category: '科幻小说',
    total: 5,
    available: true,
    cover: 'https://example.com/book1.jpg'
  },
  {
    id: 2,
    title: '百年孤独',
    author: '加西亚·马尔克斯',
    category: '文学小说',
    total: 3,
    available: true,
    cover: 'https://example.com/book2.jpg'
  },
  {
    id: 3,
    title: '活着',
    author: '余华',
    category: '当代文学',
    total: 4,
    available: false,
    cover: 'https://example.com/book3.jpg'
  },
  {
    id: 4,
    title: '人类简史',
    author: '尤瓦尔·赫拉利',
    category: '历史',
    total: 6,
    available: true,
    cover: 'https://example.com/book4.jpg'
  },
  {
    id: 5,
    title: '算法导论',
    author: 'Thomas H. Cormen',
    category: '计算机科学',
    total: 3,
    available: true,
    cover: 'https://example.com/book5.jpg'
  },
  {
    id: 6,
    title: '围城',
    author: '钱钟书',
    category: '文学小说',
    total: 4,
    available: true,
    cover: 'https://example.com/book6.jpg'
  },
  {
    id: 7,
    title: '深入理解计算机系统',
    author: 'Randal E. Bryant',
    category: '计算机科学',
    total: 2,
    available: false,
    cover: 'https://example.com/book7.jpg'
  },
  {
    id: 8,
    title: '红楼梦',
    author: '曹雪芹',
    category: '古典文学',
    total: 5,
    available: true,
    cover: 'https://example.com/book8.jpg'
  }
])

const searchQuery = ref('')

// 根据搜索关键词过滤图书
const filteredBooks = computed(() => {
  const query = searchQuery.value.toLowerCase().trim()
  if (!query) return books.value

  return books.value.filter(book =>
    book.title.toLowerCase().includes(query) ||
    book.author.toLowerCase().includes(query) ||
    book.category.toLowerCase().includes(query)
  )
})

const handleSearch = () => {
  // 这里可以添加搜索相关的逻辑
  // 比如调用API进行搜索等
}
</script>
