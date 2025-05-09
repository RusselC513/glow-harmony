<template>
  <div class="box">
    <div class="mx-auto max-w-2xl text-center">
      <h2 class="text-4xl font-semibold tracking-tight text-balance text-gray-900 sm:text-3xl">
        House Cleaning Price
      </h2>
      <p class="mt-3">Get a fast quote for your next home refresh</p>
    </div>
    <form @submit.prevent="enviarFormulario" class="mx-auto mt-16 max-w-xl sm:mt-5">
      <div class="grid grid-cols-1 gap-x-5 gap-y-4 sm:grid-cols-2">
        <div>
          <div class="mt-1.5">
            <label for="Bathrooms">Bathrooms</label>
            <select v-model="bathrooms" name="bathrooms" id="bathrooms" class="block w-full rounded-md bg-white px-3.5 py-2 text-base text-gray-900 outline-1 -outline-offset-1 outline-gray-300 placeholder:text-gray-400 focus:outline-2 focus:-outline-offset-2">
              <option value="1">1</option>
              <option value="2">2</option>
              <option value="3">3</option>
              <option value="4">4</option>
            </select>
            <span class="text-red-500 text-sm">{{ bathroomsError }}</span>
          </div>
        </div>
        <div>
          <div class="mt-1.5">
            <label for="Bedrooms">Bedrooms</label>
            <select v-model="bedrooms" name="bedrooms" id="bedrooms" class="block w-full rounded-md bg-white px-3.5 py-2 text-base text-gray-900 outline-1 -outline-offset-1 outline-gray-300 placeholder:text-gray-400 focus:outline-2 focus:-outline-offset-2">
              <option value="1">1</option>
              <option value="2">2</option>
              <option value="3">3</option>
              <option value="4">4</option>
            </select>
            <span class="text-red-500 text-sm">{{ bedroomsError }}</span>
          </div>
        </div>
        <div>
          <div class="mt-1.5">
            <label for="name">Name</label>
            <input v-model="name" type="text" name="name" id="name" placeholder="" autocomplete="given-name" class="block w-full rounded-md bg-white px-3.5 py-2 text-base text-gray-900 outline-1 -outline-offset-1 outline-gray-300 placeholder:text-gray-400 focus:outline-2 focus:-outline-offset-2">
            <span class="text-red-500 text-sm">{{ nameError }}</span>
          </div>
        </div>
        <div>
          <div class="mt-1.5">
            <label for="phone">Phone</label>
            <input v-model="phone" type="text" name="phone" id="number" autocomplete="given-number" class="block w-full rounded-md bg-white px-3.5 py-2 text-base text-gray-900 outline-1 -outline-offset-1 outline-gray-300 placeholder:text-gray-400 focus:outline-2 focus:-outline-offset-2">
            <span class="text-red-500 text-sm">{{ phoneError }}</span>
          </div>
        </div>
        <div class="sm:col-span-2">
          <div class="mt-1.5">
            <label for="email">Email</label>
            <input v-model="email" type="email" name="email" id="email" autocomplete="email" class="block w-full rounded-md bg-white px-3.5 py-2 text-base text-gray-900 outline-1 -outline-offset-1 outline-gray-300 placeholder:text-gray-400 focus:outline-2 focus:-outline-offset-2">
            <span class="text-red-500 text-sm">{{ emailError }}</span>
          </div>
        </div>
      </div>
      <div class="mt-10">
        <button type="submit" class="block w-full rounded-md px-3.5 py-2.5 text-center text-sm font-semibold text-white shadow-xs focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">GET A QUOTE</button>
      </div>
    </form>
  </div>
</template>

<style lang="scss">
form {
  button {
    background-color: $primary-color;
  }
  button:hover {
    opacity: 0.9;
  }
}
.box {
  background-color: $fondo-formulario;
  padding: 30px 40px;
  margin: 40px 30px;
  box-shadow: 0 5px 10px rgba(0, 0, 0, .15);
}
</style>




<script lang="ts" setup>
import { useForm, useField } from 'vee-validate'
import * as yup from 'yup'
import { collection, addDoc } from 'firebase/firestore'

const { $db } = useNuxtApp()

// Esquema de validación
const schema = yup.object({
  name: yup.string().required('Name is required'),
  email: yup.string().email('Invalid email').required('Email is required'),
  phone: yup.string().required('Phone is required'),
  bedrooms: yup.string().required(),
  bathrooms: yup.string().required(),
})

// Configurar el formulario
const { handleSubmit } = useForm({ validationSchema: schema })

// Campos individuales
const { value: name, errorMessage: nameError } = useField<string>('name')
const { value: email, errorMessage: emailError } = useField<string>('email')
const { value: phone, errorMessage: phoneError } = useField<string>('phone')
const { value: bedrooms, errorMessage: bedroomsError } = useField<string>('bedrooms')
const { value: bathrooms, errorMessage: bathroomsError } = useField<string>('bathrooms')

const enviarFormulario = handleSubmit(async (values) => {
  try {
    await addDoc(collection($db, 'quotes'), values)
    alert('Datos enviados correctamente')
  } catch (error) {
    console.error('Error al enviar:', error)
  }
})
</script>
