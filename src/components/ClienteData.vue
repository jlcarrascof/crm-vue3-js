<script setup>
import { computed } from 'vue'
import { RouterLink } from 'vue-router'

const props = defineProps({
  cliente: {
    type: Object,
  },
})

const direccionCompleta = computed(() => {
  return props.cliente.address + ', ' + props.cliente.country
})

const estadoCliente = computed(() => {
  return props.cliente.status
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
    <td class="whitespace-nowrap px-3 py-4 text-sm">{{ direccionCompleta }}</td>
    <td class="whitespace-nowrap px-3 py-4 text-sm">
      <button
        class="inline-flex rounded-full px-2 text-xs font-semibold leading-5"
        :class="[estadoCliente ? 'bg-green-100 text-green-800' : 'bg-red-100 text-red-800']"
      >
        {{ estadoCliente ? 'Active' : 'Inactive' }}
      </button>
    </td>
    <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">
      <RouterLink
        :to="{ name: 'editar-cliente', params: { id: cliente.id } }"
        class="text-indigo-600 hover:text-indigo-900 mr-5"
        >Edit</RouterLink
      >
      <button class="text-red-600 hover:text-red-900">Delete</button>
    </td>
  </tr>
</template>
