<template>
  <div class="min-h-screen bg-gray-50">
    <Header />
    <div class="container mx-auto px-4 py-8 mt-16">
      <!-- 返回按钮 -->
      <button
        @click="router.back()"
        class="mb-6 flex items-center text-gray-600 hover:text-blue-600"
      >
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-1" viewBox="0 0 20 20" fill="currentColor">
          <path fill-rule="evenodd" d="M9.707 16.707a1 1 0 01-1.414 0l-6-6a1 1 0 010-1.414l6-6a1 1 0 011.414 1.414L5.414 9H17a1 1 0 110 2H5.414l4.293 4.293a1 1 0 010 1.414z" clip-rule="evenodd" />
        </svg>
        返回图书列表
      </button>

      <!-- 图书详情 -->
      <div class="bg-white rounded-lg shadow-md p-6 mb-8">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <!-- 图书封面 -->
          <div class="md:col-span-1">
            <img :src="book.cover" :alt="book.title" class="w-full rounded-lg shadow-md">
          </div>

          <!-- 图书信息 -->
          <div class="md:col-span-2">
            <h1 class="text-3xl font-bold text-gray-800 mb-4">{{ book.title }}</h1>
            <div class="space-y-3">
              <div class="flex items-center gap-2">
                <span class="px-2 py-1 bg-blue-100 text-blue-600 text-sm rounded-full">{{ book.category }}</span>
                <span v-if="book.available" class="px-2 py-1 bg-green-100 text-green-600 text-sm rounded-full">可借阅</span>
                <span v-else class="px-2 py-1 bg-red-100 text-red-600 text-sm rounded-full">已借出</span>
              </div>
              <p class="text-gray-600"><span class="font-semibold">作者：</span>{{ book.author }}</p>
              <p class="text-gray-600"><span class="font-semibold">馆藏数量：</span>{{ book.total }}</p>
              <p class="text-gray-600"><span class="font-semibold">ISBN：</span>{{ book.isbn }}</p>
              <p class="text-gray-600"><span class="font-semibold">出版社：</span>{{ book.publisher }}</p>
              <p class="text-gray-600"><span class="font-semibold">出版日期：</span>{{ book.publishDate }}</p>
              <div class="mt-6">
                <button
                  class="px-6 py-2 bg-blue-500 text-white rounded-md hover:bg-blue-600 transition-colors duration-300"
                  :disabled="!book.available"
                  :class="{'opacity-50 cursor-not-allowed': !book.available}"
                >
                  借阅此书
                </button>
              </div>
            </div>
          </div>
        </div>

        <!-- 图书简介 -->
        <div class="mt-8">
          <h2 class="text-xl font-bold text-gray-800 mb-4">图书简介</h2>
          <p class="text-gray-600 leading-relaxed">{{ book.description }}</p>
        </div>
      </div>

      <!-- 评论区 -->
      <div class="bg-white rounded-lg shadow-md p-6">
        <h2 class="text-xl font-bold text-gray-800 mb-6">读者评论</h2>

        <!-- 评论列表添加固定高度和滚动效果 -->
        <div class="mb-8 h-[400px] overflow-y-auto scrollbar-thin scrollbar-thumb-gray-300 scrollbar-track-gray-100">
          <div class="space-y-6">
            <div v-for="comment in comments" :key="comment.id" class="border-b border-gray-200 pb-6 last:border-0 px-2">
              <div class="flex items-center justify-between mb-2">
                <div class="flex items-center">
                  <img :src="comment.avatar" :alt="comment.username" class="w-8 h-8 rounded-full">
                  <span class="ml-2 font-semibold text-gray-800">{{ comment.username }}</span>
                </div>
                <span class="text-sm text-gray-500">{{ comment.date }}</span>
              </div>
              <p class="text-gray-600">{{ comment.content }}</p>
            </div>
          </div>
        </div>

        <!-- 发表评论 -->
        <div class="mt-8 border-t border-gray-200 pt-6">
          <h3 class="text-lg font-semibold text-gray-800 mb-4">发表评论</h3>
          <textarea
            v-model="newComment"
            rows="3"
            placeholder="写下你的评论..."
            class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent"
          ></textarea>
          <div class="mt-2 flex justify-end">
            <button
              @click="submitComment"
              class="px-4 py-2 bg-blue-500 text-white rounded-md hover:bg-blue-600 transition-colors duration-300"
            >
              发表评论
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRouter, useRoute } from 'vue-router'
import Header from '../components/header.vue'

const router = useRouter()
const route = useRoute()
const newComment = ref('')

// 模拟图书详情数据
const book = ref({
  id: 1,
  title: '三体',
  author: '刘慈欣',
  category: '科幻小说',
  total: 5,
  available: true,
  cover: 'https://example.com/book1.jpg',
  isbn: '9787536692930',
  publisher: '重庆出版社',
  publishDate: '2008-01-01',
  description: '文化大革命期间，一次偶然的机会，南京大学天体物理系女教授叶文洁参与了一项绝密军事工程，代号"红岸工程"。她的一个简单的决定，影响了人类的命运...'
})

// 更新模拟评论数据，添加更多评论
const comments = ref([
  {
    id: 1,
    username: '文学爱好者',
    avatar: 'https://example.com/avatar1.jpg',
    content: '这本书真的很棒，让我对宇宙有了全新的认识！看完第一部就迫不及待想看第二部了。',
    date: '2024-03-15'
  },
  {
    id: 2,
    username: '科幻迷',
    avatar: 'https://example.com/avatar2.jpg',
    content: '刘慈欣的想象力真是太丰富了，强烈推荐！整个三体系列都值得一读。',
    date: '2024-03-14'
  },
  {
    id: 3,
    username: '阅读达人',
    avatar: 'https://example.com/avatar3.jpg',
    content: '这是一部改变我世界观的作品，让我重新思考人类文明的发展方向。',
    date: '2024-03-13'
  },
  {
    id: 4,
    username: '书虫一枚',
    avatar: 'https://example.com/avatar4.jpg',
    content: '很庆幸能读到这样的作品，情节跌宕起伏，充满哲学思考。',
    date: '2024-03-12'
  },
  {
    id: 5,
    username: '悠闲读者',
    avatar: 'https://example.com/avatar5.jpg',
    content: '第一次读科幻小说就被震撼到了，作者的脑洞太大了！',
    date: '2024-03-11'
  },
  {
    id: 6,
    username: '夜读人',
    avatar: 'https://example.com/avatar6.jpg',
    content: '看完这本书后，我开始关注天文学和物理学，太有意思了！',
    date: '2024-03-10'
  },
  {
    id: 7,
    username: '读书笔记',
    avatar: 'https://example.com/avatar7.jpg',
    content: '这本书的翻译很棒，没有生涩感，读起来很流畅。',
    date: '2024-03-09'
  },
  {
    id: 8,
    username: '科学迷',
    avatar: 'https://example.com/avatar8.jpg',
    content: '书中对三体文明的描写非常独特，让人印象深刻。',
    date: '2024-03-08'
  }
])

// 提交评论
const submitComment = () => {
  if (!newComment.value.trim()) return

  comments.value.unshift({
    id: comments.value.length + 1,
    username: '当前用户',
    avatar: 'https://example.com/avatar-default.jpg',
    content: newComment.value,
    date: new Date().toISOString().split('T')[0]
  })

  newComment.value = ''
}

// 获取图书详情
onMounted(async () => {
  const bookId = route.params.id
  // 这里应该调用API获取图书详情
  // const response = await fetch(`/api/books/${bookId}`)
  // book.value = await response.json()
})
</script>

<style>
/* 自定义滚动条样式 */
.scrollbar-thin::-webkit-scrollbar {
  width: 6px;
}

.scrollbar-thin::-webkit-scrollbar-track {
  background: #f1f1f1;
  border-radius: 3px;
}

.scrollbar-thin::-webkit-scrollbar-thumb {
  background: #d1d5db;
  border-radius: 3px;
}

.scrollbar-thin::-webkit-scrollbar-thumb:hover {
  background: #9ca3af;
}
</style>
