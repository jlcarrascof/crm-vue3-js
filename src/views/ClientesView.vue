<script setup>
import { onMounted, ref, computed } from 'vue'
import axios from 'axios'
import UiHeading from '../components/UI/UiHeading.vue'
import RouterLink from '../components/UI/RouterLink.vue'

const clientes = ref([])

onMounted(() => {
  axios
    .get('http://localhost:4000/clientes/')
    .then(({ data }) => (clientes.value = data))
    .catch((error) => console.log('There is an error', error))
})

defineProps({
  titulo: {
    type: String,
  },
})

const existenClientes = computed(() => {
  return clientes.value.length > 0
})
</script>

<template>
  <div>
    <div class="flex justify-end">
      <RouterLink to="agregar-cliente"> Add Customer </RouterLink>
    </div>

    <UiHeading>{{ titulo }}</UiHeading>

    <div v-if="existenClientes">
      <p>We have customers!!</p>
    </div>

    <p v-else class="text-center mt-10">There aren't customers</p>
  </div>
</template>
