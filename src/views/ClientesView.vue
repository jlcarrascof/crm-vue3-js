<script setup>
import { onMounted } from 'vue'
import axios from 'axios'
import UiHeading from '../components/UI/UiHeading.vue'
import RouterLink from '../components/UI/RouterLink.vue'

onMounted(() => {
  axios
    .get('http://localhost:4000/clientes/')
    .then(({ data }) => {
      console.log(data)
    })
    .catch((error) => console.log('There is an error', error))
})

defineProps({
  titulo: {
    type: String,
  },
})
</script>

<template>
  <div>
    <div class="flex justify-end">
      <RouterLink to="agregar-cliente"> Add Customer </RouterLink>
    </div>
    <UiHeading>{{ titulo }}</UiHeading>
  </div>
</template>
