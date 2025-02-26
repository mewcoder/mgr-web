<template>
  <div class="page-container">
    <Header />
    <div class="points-exchange-page">
      <!-- 积分显示区域 -->
      <div class="points-header">
        <div class="points-balance">
          <h2>我的积分</h2>
          <div class="points-amount">
            <span class="number">{{ userPoints }}</span>
            <span class="unit">积分</span>
          </div>
        </div>
      </div>

      <!-- 商品列表区域 -->
      <div class="products-section">
        <h2>可兑换商品</h2>
        <div class="products-grid">
          <div v-for="product in products" :key="product.id" class="product-card">
            <div class="status-badge" v-if="product.status === 'soldout'">已抢光</div>
            <div class="status-badge insufficient" v-else-if="userPoints < product.points">积分不足</div>
            <img :src="product.image" :alt="product.name" class="product-image">
            <div class="product-info">
              <h3>{{ product.name }}</h3>
              <p class="points-required">{{ product.points }} 积分</p>
              <button
                @click="exchangeProduct(product)"
                :disabled="userPoints < product.points || product.status === 'soldout'"
                class="exchange-btn"
              >
                {{ product.status === 'soldout' ? '已抢光' : '立即兑换' }}
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Header from '../components/header.vue'

// 用户积分（实际项目中应该从API获取）
const userPoints = ref(1000)

// 商品列表（实际项目中应该从API获取）
const products = ref([
  {
    id: 1,
    name: '优惠券 ¥10',
    points: 100,
    image: '/images/coupon.png',
    status: 'available'
  },
  {
    id: 2,
    name: '电影票',
    points: 500,
    image: '/images/movie-ticket.png',
    status: 'available'
  },
  {
    id: 3,
    name: '咖啡券',
    points: 300,
    image: '/images/coffee.png',
    status: 'soldout'
  },
  {
    id: 4,
    name: '蓝牙耳机',
    points: 2000,
    image: '/images/headphones.png',
    status: 'available'
  },
  {
    id: 5,
    name: '午餐券',
    points: 200,
    image: '/images/lunch.png',
    status: 'available'
  },
  {
    id: 6,
    name: '健身月卡',
    points: 1500,
    image: '/images/gym.png',
    status: 'available'
  },
  {
    id: 7,
    name: '按摩券',
    points: 800,
    image: '/images/massage.png',
    status: 'soldout'
  },
  {
    id: 8,
    name: '超市购物券',
    points: 400,
    image: '/images/shopping.png',
    status: 'available'
  }
])

// 兑换商品方法
const exchangeProduct = (product) => {
  if (userPoints.value >= product.points) {
    // 这里应该调用API进行兑换
    if (confirm(`确定要使用 ${product.points} 积分兑换 ${product.name} 吗？`)) {
      userPoints.value -= product.points
      alert('兑换成功！')
    }
  } else {
    alert('积分不足！')
  }
}
</script>

<style scoped>
.page-container {
  min-height: 100vh;
  background-color: #f9fafb;
}

.points-exchange-page {
  padding: 20px;
  padding-top: 80px; /* 添加顶部内边距，为 header 留出空间 */
  max-width: 1200px;
  margin: 0 auto;
}

.points-header {
  background: linear-gradient(135deg, #6366f1, #8b5cf6);
  color: white;
  padding: 30px;
  border-radius: 12px;
  margin-bottom: 30px;
}

.points-balance {
  text-align: center;
}

.points-amount {
  margin-top: 10px;
}

.points-amount .number {
  font-size: 36px;
  font-weight: bold;
}

.points-amount .unit {
  font-size: 18px;
  margin-left: 5px;
}

.products-section h2 {
  margin-bottom: 20px;
}

.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
  gap: 20px;
  padding: 0 10px;
}

@media (min-width: 1024px) {
  .products-grid {
    grid-template-columns: repeat(4, 1fr);
  }
}

.product-card {
  position: relative;
  border: 1px solid #e5e7eb;
  border-radius: 8px;
  overflow: hidden;
  transition: transform 0.2s;
  background: white;
}

.status-badge {
  position: absolute;
  top: 10px;
  right: 10px;
  padding: 4px 8px;
  background-color: #ef4444;
  color: white;
  border-radius: 4px;
  font-size: 12px;
  font-weight: bold;
  z-index: 1;
}

.status-badge.insufficient {
  background-color: #f59e0b;
}

.product-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.product-image {
  width: 100%;
  height: 200px;
  object-fit: cover;
  opacity: 1;
  transition: opacity 0.2s;
}

/* 已抢光商品的暗化效果 */
.product-card[data-status="soldout"] .product-image {
  opacity: 0.6;
}

.product-info {
  padding: 15px;
}

.product-info h3 {
  margin: 0 0 10px 0;
  font-size: 18px;
}

.points-required {
  color: #6366f1;
  font-weight: bold;
  margin-bottom: 10px;
}

.exchange-btn {
  width: 100%;
  padding: 8px;
  background-color: #6366f1;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.2s;
}

.exchange-btn:hover:not(:disabled) {
  background-color: #4f46e5;
}

.exchange-btn:disabled {
  background-color: #9ca3af;
  cursor: not-allowed;
  opacity: 0.8;
}

.product-card[data-status="soldout"] .exchange-btn {
  background-color: #6b7280;
}
</style>
