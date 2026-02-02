<script setup>
import RouterLink from '../components/UI/RouterLink.vue'
import UiHeading from '../components/UI/UiHeading.vue'

defineProps({
  titulo: {
    type: String,
  },
})
</script>

<template>
  <div>
    <div class="flex justify-end">
      <RouterLink to="inicio"> Return </RouterLink>
    </div>

    <UiHeading>{{ titulo }}</UiHeading>
  </div>
</template>
