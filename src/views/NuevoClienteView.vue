<script setup>
import { RouterLink } from 'vue-router'
</script>

<template>
  <div>
    <RouterLink :to="{ name: 'inicio' }"> Return </RouterLink>
  </div>

  <div>
    <h1 class="text-4xl font-extrabold text-slate-500">Add Clients</h1>
  </div>
</template>
