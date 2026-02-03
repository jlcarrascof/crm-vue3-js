<script setup>
import { onMounted, ref, computed } from 'vue'
import ClienteService from '../services/ClienteService'
import UiHeading from '../components/UI/UiHeading.vue'
import RouterLink from '../components/UI/RouterLink.vue'
import ClienteData from '../components/ClienteData.vue'

const clientes = ref([])

onMounted(() => {
  ClienteService.obtenerClientes()
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

    <div v-if="existenClientes" class="flow-root mx-auto mt-10 p-5 bg-white shadow">
      <div class="-my-2 -mx-4 overflow-x-auto sm:-mx-6 lg:-mx-8">
        <div class="min-w-full py-2 align-middle sm:px-6 lg:px-8">
          <table class="min-w-full divide-y divide-gray-300">
            <thead>
              <tr>
                <th scope="col" class="p-2 text-left text-sm font-extrabold text-gray-600">
                  Customer
                </th>
                <th scope="col" class="p-2 text-left text-sm font-extrabold text-gray-600">
                  Email
                </th>
                <th scope="col" class="p-2 text-left text-sm font-extrabold text-gray-600">
                  City, Country
                </th>
                <th scope="col" class="p-2 text-left text-sm font-extrabold text-gray-600">
                  Actions
                </th>
              </tr>
            </thead>
            <tbody class="divide-y divide-gray-200 bg-white">
              <ClienteData v-for="cliente in clientes" :key="cliente.id" :cliente="cliente" />
            </tbody>
          </table>
        </div>
      </div>
    </div>

    <p v-else class="text-center mt-10">There aren't customers</p>
  </div>
</template>
