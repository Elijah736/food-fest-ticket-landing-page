<template>
  <div class="container">
    <Header :wishlistCount="wishlist.length" />

    <CourseList
      :courses="tickets"
      @save-course="Tickets"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import Header from './components/hero.vue';
import Tickets from './components/tickets.vue';
import tickets from './tickets';

const wishlist = ref([])

function saveticket(id) {
  if (!wishlist.value.includes(id)) {
    wishlist.value.push(id)
  }
}
</script>
