<script setup>
import { FormKit } from '@formkit/vue'
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

    <div class="mx-auto mt-10 bg-slate-200 shadow">
      <div class="mx-auto md:w-2/3 py-20 px-6">
        <FormKit type="form">
          <FormKit
            type="text"
            label="Customer"
            placeholder="Customer description"
            validation="required"
            :validation-messages="{ required: 'Customer name is mandatory' }"
          />

          <FormKit
            type="text"
            label="Email"
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
            placeholder="Phone number: XXX-XXX-XXXXXXX"
            validation="*matches:/^[0-9]{3}-[0-9]{3}-[0-9]{7}$/"
            :validation-messages="{
              matches: 'Telephone format is not valid',
            }"
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
