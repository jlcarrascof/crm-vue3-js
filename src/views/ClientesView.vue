<script setup>
import { RouterLink } from 'vue-router'
</script>

<template>
  <div>
    <div>
      <RouterLink :to="{ name: 'agregar-cliente' }"> Add Customer </RouterLink>
    </div>

    <h1 class="text-4xl font-extrabold text-slate-500">Clients</h1>
  </div>
</template>
