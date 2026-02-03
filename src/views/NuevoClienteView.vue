<script setup>
import axios from 'axios'
import { useRouter } from 'vue-router'
import { FormKit } from '@formkit/vue'
import RouterLink from '../components/UI/RouterLink.vue'
import UiHeading from '../components/UI/UiHeading.vue'

const router = useRouter()

defineProps({
  titulo: {
    type: String,
  },
})

const handleSubmit = (data) => {
  axios
    .post('http://localhost:4000/clientes/', data)
    .then((respuesta) => {
      console.log(respuesta)
      // redireccionar
      router.push({ name: 'listado-clientes' })
    })
    .catch((error) => console.log(error))
}
</script>

<template>
  <div>
    <div class="flex justify-end">
      <RouterLink to="inicio"> Return </RouterLink>
    </div>

    <UiHeading>{{ titulo }}</UiHeading>

    <div class="mx-auto mt-10 bg-slate-200 shadow">
      <div class="mx-auto md:w-2/3 py-20 px-6">
        <FormKit
          type="form"
          submit-label="Add New Customer"
          incomplete-message="Impossible to send! Check the form"
          @submit="handleSubmit"
        >
          <FormKit
            type="text"
            label="Customer"
            name="customer"
            placeholder="Customer description"
            validation="required"
            :validation-messages="{ required: 'Customer name is mandatory' }"
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
          />

          <FormKit type="text" label="Address" name="address" placeholder="Customer address" />

          <FormKit type="text" label="Country" name="country" placeholder="Customer country" />
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
