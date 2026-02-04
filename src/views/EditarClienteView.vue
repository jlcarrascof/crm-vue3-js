<script setup>
import { onMounted, reactive } from 'vue'
import ClienteService from '../services/ClienteService'
import { useRouter, useRoute } from 'vue-router'
import { FormKit } from '@formkit/vue'
import RouterLink from '../components/UI/RouterLink.vue'
import UiHeading from '../components/UI/UiHeading.vue'

const router = useRouter()
const route = useRoute()

const { id } = route.params

const formData = reactive({})

onMounted(() => {
  ClienteService.obtenerCliente(id)
    .then(({ data }) => {
      Object.assign(formData, data)
    })
    .catch((error) => console.log(error))
})

defineProps({
  titulo: {
    type: String,
  },
})

const handleSubmit = (data) => {
  ClienteService.actualizarCliente(id, data)
    .then(() => router.push({ name: 'listado-clientes' }))
    .catch((error) => console.log(error))
}
</script>

<template>
  <div>
    <div class="flex justify-end">
      <RouterLink to="listado-clientes"> Return </RouterLink>
    </div>

    <UiHeading>{{ titulo }}</UiHeading>

    <div class="mx-auto mt-10 bg-slate-200 shadow">
      <div class="mx-auto md:w-2/3 py-20 px-6">
        <FormKit
          type="form"
          submit-label="Add New Customer"
          incomplete-message="Impossible to send! Check the form"
          @submit="handleSubmit"
          :value="formData"
        >
          <FormKit
            type="text"
            label="Customer"
            name="customer"
            placeholder="Customer description"
            validation="required"
            :validation-messages="{ required: 'Customer name is mandatory' }"
            v-model="formData.customer"
          />

          <FormKit
            type="text"
            label="Email"
            name="email"
            placeholder="Customer email"
            validation="required|email"
            :validation-messages="{
              required: 'Customer email is mandatory',
              email: 'Enter a valid email',
            }"
            v-model="formData.email"
          />

          <FormKit
            type="text"
            label="Phone Number"
            name="phone"
            placeholder="Phone number: XXX-XXX-XXXXXXX"
            validation="*matches:/^[0-9]{3}-[0-9]{3}-[0-9]{7}$/"
            :validation-messages="{
              matches: 'Telephone format is not valid',
            }"
            v-model="formData.phone"
          />

          <FormKit
            type="text"
            label="Address"
            name="address"
            placeholder="Customer address"
            v-model="formData.address"
          />

          <FormKit
            type="text"
            label="Country"
            name="country"
            placeholder="Customer country"
            v-model="formData.country"
          />
        </FormKit>
      </div>
    </div>
  </div>
</template>

<style>
.formkit-wrapper {
  max-width: 100%;
}
</style>
