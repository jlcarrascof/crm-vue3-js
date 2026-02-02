<script setup>
import { RouterLink } from 'vue-router'
</script>

<template>
  <RouterLink
    :to="{ name: 'agregar-cliente' }"
    class="block md:inline-block rounded bg-blue-600 py-2 px-3"
  >
    Add Customer
  </RouterLink>
</template>
