<script setup>
import { ref } from 'vue'
import { Carousel, Slide, Navigation } from 'vue3-carousel'
import 'vue3-carousel/dist/carousel.css'

const activities = ref([
  {
    id: 1,
    title: '暑期阅读马拉松',
    image: '/images/activity1.jpg',
    date: '2024-07-01',
    description: '暑期两个月，和小伙伴一起阅读打卡，累计阅读天数最多的读者可获得精美奖品！'
  },
  {
    id: 2,
    title: '世界读书日特别活动',
    image: '/images/activity2.jpg',
    date: '2024-04-23',
    description: '4月23日世界读书日，参与读书分享会，还有精选图书抽奖活动等你来！'
  },
  {
    id: 3,
    title: '名家讲座：与作家对话',
    image: '/images/activity3.jpg',
    date: '2024-05-15',
    description: '著名作家王某某将来到图书馆，与读者分享创作经验和阅读心得。'
  },
  {
    id: 4,
    title: '亲子阅读工作坊',
    image: '/images/activity4.jpg',
    date: '2024-06-01',
    description: '六一儿童节特别活动，邀请专业老师指导家长如何与孩子共读绘本。'
  },
  {
    id: 5,
    title: '图书跳蚤市场',
    image: '/images/activity5.jpg',
    date: '2024-05-28',
    description: '以旧换新，让书籍流转起来！带上您的旧书来参加跳蚤市场吧。'
  }
])
</script>

<template>
  <div class="bg-white rounded-lg shadow-md p-4">
    <h2 class="text-xl font-bold mb-4">近期活动</h2>
    <div class="relative">
      <Carousel
        :items-to-show="2"
        :items-to-scroll="1"
        :wrap-around="true"
        :transition="500"
        :autoplay="3000"
        :pause-autoplay-on-hover="true"
        class="h-[380px]"
        snapAlign="start"
      >
        <Slide v-for="activity in activities" :key="activity.id">
          <div class="carousel__item mx-2">
            <div class="bg-gray-50 rounded-lg overflow-hidden h-full shadow hover:shadow-md transition-shadow">
              <img :src="activity.image"
                   :alt="activity.title"
                   class="w-full h-48 object-cover"
                   onerror="this.src='https://picsum.photos/400/200'" />
              <div class="p-4">
                <h3 class="font-semibold text-lg mb-2">{{ activity.title }}</h3>
                <p class="text-gray-600 mb-2 line-clamp-2">{{ activity.description }}</p>
                <p class="text-blue-600">开始时间：{{ activity.date }}</p>
              </div>
            </div>
          </div>
        </Slide>

        <template #addons>
          <Navigation />
        </template>
      </Carousel>
    </div>
  </div>
</template>

<style scoped>
.carousel__item {
  height: 100%;
}

:deep(.carousel__slide) {
  padding: 1px;
}

:deep(.carousel__prev),
:deep(.carousel__next) {
  background-color: rgba(0, 0, 0, 0.3);
  border-radius: 50%;
  width: 40px;
  height: 40px;
  color: white;
  margin: 0 10px;
}

:deep(.carousel__prev:hover),
:deep(.carousel__next:hover) {
  background-color: rgba(0, 0, 0, 0.5);
}

:deep(.carousel__track) {
  padding: 10px 0;
}
</style>
