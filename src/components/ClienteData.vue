<script setup>
import { computed } from 'vue'
import { RouterLink } from 'vue-router'

const props = defineProps({
  cliente: {
    type: Object,
  },
})

const nombreCliente = computed(() => {
  return props.cliente.address + ', ' + props.cliente.country
})
</script>

<template>
  <tr>
    <td class="whitespace-nowrap py-4 pl-4 pr-3 text-sm sm:pl-0">
      <!--
      <p class="font-medium text-gray-900">{{ nombreCliente }}</p>
      -->
      <p class="font-medium text-gray-900">{{ cliente.customer }}</p>
      <p class="text-gray-500"></p>
    </td>
    <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">
      <p class="text-gray-900 font-bold">{{ cliente.email }}</p>
      <p class="text-gray-600"></p>
    </td>
    <td class="whitespace-nowrap px-3 py-4 text-sm">{{ nombreCliente }}</td>
    <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">
      <RouterLink to="/" class="text-indigo-600 hover:text-indigo-900 mr-5">Edit</RouterLink>
      <button class="text-red-600 hover:text-red-900">Delete</button>
    </td>
  </tr>
</template>
