<template>
  <HeroSection />

  <section id="tickets" class="tickets">
    <h2>Choose Your Experience</h2>

    <div class="ticket-grid">
      <TicketCard
        v-for="ticket in tickets"
        :key="ticket.id"
        :ticket="ticket"
      />
    </div>
  </section>
</template>

<script setup>
import HeroSection from './components/hero.vue'
import TicketCard from './components/ticketlist.vue'
import tickets from './tickets'
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: Arial, sans-serif;
  background: #f5f5f5;
}

.tickets {
  padding: 4rem 2rem;
}

.tickets h2 {
  text-align: center;
  margin-bottom: 2rem;
}

.ticket-grid {
  display: grid;
  gap: 2rem;
  grid-template-columns:
    repeat(auto-fit, minmax(280px, 1fr));
}

@media (max-width: 768px) {
  .ticket-grid {
    grid-template-columns: 1fr;
  }
}
</style>