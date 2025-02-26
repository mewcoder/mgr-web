<template>
  <div class="min-h-screen bg-gray-100">
    <!-- 顶部个人信息卡片 -->
    <div class="w-full bg-white shadow-md px-4 py-6 mb-6">
      <div class="max-w-7xl mx-auto">
        <div class="flex items-center space-x-6">
          <div class="relative">
            <img
              :src="userInfo.avatar || '/default-avatar.png'"
              class="w-24 h-24 rounded-full object-cover"
              alt="用户头像"
            />
            <button
              @click="editAvatar"
              class="absolute bottom-0 right-0 bg-blue-500 text-white p-1 rounded-full"
            >
              <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15.232 5.232l3.536 3.536m-2.036-5.036a2.5 2.5 0 113.536 3.536L6.5 21.036H3v-3.572L16.732 3.732z" />
              </svg>
            </button>
          </div>
          <div class="flex-1">
            <div class="flex items-center justify-between">
              <div>
                <h2 class="text-2xl font-bold">{{ userInfo.name }}</h2>
                <div class="mt-2 flex items-center space-x-4 text-gray-600">
                  <span>会员等级：{{ userInfo.level }}</span>
                  <span>积分：{{ userInfo.points }}</span>
                  <span>注册时间：2024-01-01</span>
                </div>
              </div>
              <button
                @click="showEditModal = true"
                class="bg-blue-500 text-white px-4 py-2 rounded-md hover:bg-blue-600"
              >
                编辑资料
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- 主要内容区 -->
    <div class="max-w-7xl mx-auto px-4">
      <div class="flex gap-6">
        <!-- 左侧导航 -->
        <div class="w-48 flex-shrink-0">
          <div class="bg-white rounded-lg shadow-md overflow-hidden">
            <nav class="space-y-1">
              <button
                v-for="tab in tabs"
                :key="tab.id"
                @click="currentTab = tab.id"
                :class="[
                  'w-full px-4 py-3 flex items-center space-x-2 text-left',
                  currentTab === tab.id
                    ? 'bg-blue-50 text-blue-600 border-l-4 border-blue-500'
                    : 'text-gray-700 hover:bg-gray-50'
                ]"
              >
                <component :is="tab.icon" class="w-5 h-5" />
                <span>{{ tab.name }}</span>
              </button>
            </nav>
          </div>
        </div>

        <!-- 右侧内容区 -->
        <div class="flex-1 bg-white rounded-lg shadow-md p-6">
          <!-- 借阅记录 -->
          <div v-if="currentTab === 'borrowed'" class="space-y-4">
            <div class="flex justify-between items-center mb-6">
              <h3 class="text-lg font-semibold">借阅记录</h3>
              <div class="flex space-x-2">
                <select v-model="borrowFilter" class="rounded-md border-gray-300">
                  <option value="all">全部</option>
                  <option value="current">当前借阅</option>
                  <option value="history">历史借阅</option>
                </select>
              </div>
            </div>
            <table class="min-w-full divide-y divide-gray-200">
              <thead class="bg-gray-50">
                <tr>
                  <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">书名</th>
                  <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">借阅时间</th>
                  <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">应还时间</th>
                  <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">状态</th>
                  <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">操作</th>
                </tr>
              </thead>
              <tbody class="bg-white divide-y divide-gray-200">
                <tr v-for="book in filteredBorrowedBooks" :key="book.id">
                  <td class="px-6 py-4">{{ book.title }}</td>
                  <td class="px-6 py-4">{{ book.borrowDate }}</td>
                  <td class="px-6 py-4">{{ book.returnDate }}</td>
                  <td class="px-6 py-4">
                    <span :class="book.isOverdue ? 'text-red-500' : 'text-green-500'">
                      {{ book.isOverdue ? '已逾期' : '正常' }}
                    </span>
                  </td>
                  <td class="px-6 py-4">
                    <button class="text-blue-500 hover:text-blue-700">续借</button>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>

          <!-- 积分记录 -->
          <div v-if="currentTab === 'points'" class="space-y-4">
            <div class="flex justify-between items-center mb-6">
              <h3 class="text-lg font-semibold">积分记录</h3>
              <div class="flex space-x-2">
                <select v-model="pointsFilter" class="rounded-md border-gray-300">
                  <option value="all">全部</option>
                  <option value="gain">获得积分</option>
                  <option value="spend">消费积分</option>
                </select>
              </div>
            </div>
            <table class="min-w-full divide-y divide-gray-200">
              <thead class="bg-gray-50">
                <tr>
                  <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">时间</th>
                  <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">类型</th>
                  <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">描述</th>
                  <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">积分变动</th>
                </tr>
              </thead>
              <tbody class="bg-white divide-y divide-gray-200">
                <tr v-for="record in filteredPointsRecords" :key="record.id">
                  <td class="px-6 py-4">{{ record.date }}</td>
                  <td class="px-6 py-4">{{ record.type }}</td>
                  <td class="px-6 py-4">{{ record.description }}</td>
                  <td class="px-6 py-4" :class="record.points > 0 ? 'text-green-500' : 'text-red-500'">
                    {{ record.points > 0 ? '+' : '' }}{{ record.points }}
                  </td>
                </tr>
              </tbody>
            </table>
          </div>

          <!-- 活动记录 -->
          <div v-if="currentTab === 'activities'" class="space-y-4">
            <div class="flex justify-between items-center mb-6">
              <h3 class="text-lg font-semibold">活动记录</h3>
              <div class="flex space-x-2">
                <select v-model="activityFilter" class="rounded-md border-gray-300">
                  <option value="all">全部活动</option>
                  <option value="upcoming">即将开始</option>
                  <option value="completed">已结束</option>
                </select>
              </div>
            </div>
            <table class="min-w-full divide-y divide-gray-200">
              <thead class="bg-gray-50">
                <tr>
                  <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">活动名称</th>
                  <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">活动时间</th>
                  <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">活动地点</th>
                  <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">状态</th>
                  <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">操作</th>
                </tr>
              </thead>
              <tbody class="bg-white divide-y divide-gray-200">
                <tr v-for="activity in filteredActivities" :key="activity.id">
                  <td class="px-6 py-4">{{ activity.title }}</td>
                  <td class="px-6 py-4">{{ activity.date }}</td>
                  <td class="px-6 py-4">{{ activity.location }}</td>
                  <td class="px-6 py-4">
                    <span :class="getStatusClass(activity.status)">
                      {{ activity.status }}
                    </span>
                  </td>
                  <td class="px-6 py-4">
                    <button
                      v-if="activity.status === '已报名'"
                      class="text-red-500 hover:text-red-700"
                    >
                      取消报名
                    </button>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>

    <!-- 编辑个人信息模态框 -->
    <div v-if="showEditModal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center">
      <div class="bg-white rounded-lg p-6 w-full max-w-md">
        <h3 class="text-xl font-semibold mb-4">编辑个人信息</h3>
        <form @submit.prevent="updateProfile" class="space-y-4">
          <div>
            <label class="block text-sm font-medium text-gray-700">姓名</label>
            <input
              v-model="editForm.name"
              type="text"
              class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500"
            />
          </div>
          <div>
            <label class="block text-sm font-medium text-gray-700">电话</label>
            <input
              v-model="editForm.phone"
              type="tel"
              class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500"
            />
          </div>
          <div>
            <label class="block text-sm font-medium text-gray-700">邮箱</label>
            <input
              v-model="editForm.email"
              type="email"
              class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500"
            />
          </div>
          <div class="flex justify-end space-x-3">
            <button
              type="button"
              @click="showEditModal = false"
              class="px-4 py-2 border border-gray-300 rounded-md text-gray-700 hover:bg-gray-50"
            >
              取消
            </button>
            <button
              type="submit"
              class="px-4 py-2 bg-blue-500 text-white rounded-md hover:bg-blue-600"
            >
              保存
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive, computed } from 'vue'

// 标签页配置
const tabs = [
  {
    id: 'borrowed',
    name: '借阅记录',
    icon: 'BookIcon'
  },
  {
    id: 'points',
    name: '积分记录',
    icon: 'CoinIcon'
  },
  {
    id: 'activities',
    name: '活动记录',
    icon: 'CalendarIcon'
  }
]

const currentTab = ref('borrowed')
const borrowFilter = ref('all')
const pointsFilter = ref('all')
const activityFilter = ref('all')

// 用户信息
const userInfo = reactive({
  name: '张三',
  avatar: null,
  level: '黄金会员',
  points: 1250
})

// 借阅图书列表
const borrowedBooks = ref([
  {
    id: 1,
    title: '三体',
    borrowDate: '2024-03-01',
    returnDate: '2024-04-01',
    isOverdue: false
  },
  {
    id: 2,
    title: '百年孤独',
    borrowDate: '2024-02-15',
    returnDate: '2024-03-15',
    isOverdue: true
  },
  // 添加更多记录...
])

// 积分记录
const pointsRecords = ref([
  {
    id: 1,
    date: '2024-03-01',
    type: '借阅',
    description: '借阅图书',
    points: -2
  },
  {
    id: 2,
    date: '2024-02-28',
    type: '活动',
    description: '参与读书会活动',
    points: 50
  },
  // 添加更多记录...
])

// 活动记录
const activities = ref([
  {
    id: 1,
    title: '春季读书会',
    date: '2024-03-15',
    location: '图书馆报告厅',
    status: '已报名'
  },
  {
    id: 2,
    title: '新书分享会',
    date: '2024-02-20',
    location: '图书馆二楼',
    status: '已完成'
  },
  // 添加更多记录...
])

// 筛选计算属性
const filteredBorrowedBooks = computed(() => {
  if (borrowFilter.value === 'all') return borrowedBooks.value
  return borrowedBooks.value.filter(book =>
    borrowFilter.value === 'current' ? !book.isOverdue : book.isOverdue
  )
})

const filteredPointsRecords = computed(() => {
  if (pointsFilter.value === 'all') return pointsRecords.value
  return pointsRecords.value.filter(record =>
    pointsFilter.value === 'gain' ? record.points > 0 : record.points < 0
  )
})

const filteredActivities = computed(() => {
  if (activityFilter.value === 'all') return activities.value
  return activities.value.filter(activity =>
    activityFilter.value === 'upcoming'
      ? activity.status === '已报名'
      : activity.status === '已完成'
  )
})

// 编辑表单
const showEditModal = ref(false)
const editForm = reactive({
  name: userInfo.name,
  phone: '13800138000',
  email: 'zhangsan@example.com'
})

// 方法
const editAvatar = () => {
  // 实现头像上传逻辑
}

const updateProfile = () => {
  // 实现更新个人信息逻辑
  userInfo.name = editForm.name
  showEditModal.value = false
}

const getStatusClass = (status) => {
  switch (status) {
    case '已报名':
      return 'text-blue-500'
    case '已完成':
      return 'text-green-500'
    case '已取消':
      return 'text-gray-500'
    default:
      return 'text-gray-700'
  }
}
</script>
