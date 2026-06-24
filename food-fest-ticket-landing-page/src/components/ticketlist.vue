<template>
  <div
    class="ticket-card"
    :class="{ featured: ticket.featured }"
  >
    <button
      class="favorite-btn"
      @click="toggleFavorite"
    >
      {{ isFavorite ? '❤️' : '🤍' }}
    </button>

    <div v-if="ticket.featured" class="badge">
      Most Popular
    </div>

    <h2>{{ ticket.name }}</h2>

    <p class="price">
      R{{ ticket.price }}
    </p>

    <p>{{ ticket.description }}</p>

    <ul>
      <li
        v-for="benefit in ticket.benefits"
        :key="benefit"
      >
        ✓ {{ benefit }}
      </li>
    </ul>

    <button class="buy-btn">
      Coming Soon
    </button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const props = defineProps({
  ticket: Object
})

const isFavorite = ref(false)

function toggleFavorite() {
  isFavorite.value = !isFavorite.value
}
</script>

<style scoped>
.ticket-card {
  position: relative;
  background: white;
  border-radius: 16px;
  padding: 2rem;
  box-shadow: 0 4px 12px rgba(0,0,0,.1);
  transition: all .3s ease;
}

.ticket-card:hover {
  transform: translateY(-8px);
}

.featured {
  border: 3px solid #ff9800;
  transform: scale(1.05);
}

.badge {
  background: #ff9800;
  color: white;
  padding: 6px 12px;
  border-radius: 20px;
  display: inline-block;
  margin-bottom: 1rem;
}

.favorite-btn {
  position: absolute;
  top: 15px;
  right: 15px;
  border: none;
  background: transparent;
  font-size: 1.5rem;
  cursor: pointer;
}

.price {
  font-size: 2rem;
  font-weight: bold;
  color: #ff5722;
}

.buy-btn {
  width: 100%;
  padding: 12px;
  border: none;
  background: #ff5722;
  color: white;
  border-radius: 8px;
  cursor: pointer;
}
</style>