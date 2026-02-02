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

    <div class="mx-auto mt-10 bg-white shadow">
      <div class="mx-auto md:w-2/3 py-20 px-6">
        <FormKit type="form">
          <FormKit
            type="text"
            label="Customer"
            placeholder="Customer description"
            help="Type the customer name to register"
            validation="required"
            :validation-messages="{ required: 'Customer name is mandatory' }"
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
