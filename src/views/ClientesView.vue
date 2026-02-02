<script setup>
import UiHeading from '../components/UI/UiHeading.vue'
import RouterLink from '../components/UI/RouterLink.vue'
</script>

<template>
  <div>
    <div class="flex justify-end">
      <RouterLink to="agregar-cliente"> Add Customer </RouterLink>
    </div>
    <UiHeading>Clients</UiHeading>
  </div>
</template>
