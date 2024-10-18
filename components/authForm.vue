<template>
  <form
    class="py-6 space-y-4"
    @submit.prevent="handleSubmit"
  >
    <div>
      <label class="sr-only" for="name">Email</label>
      <!-- Input field e-mail -->
      <input
        class="w-96 rounded-lg border border-gray-900/10 p-3"
        placeholder="Email"
        name="email"
        type="email"
        id="email"
        required
      />
    </div>

    <div>
      <label class="sr-only" for="message">Password</label>
      <!-- Input field password -->
      <input
        class="w-96 rounded-lg border border-gray-900/10 p-3"
        placeholder="Password"
        name="password"
        type="password"
        id="description"
        required
      ></input>
    </div>

    <div class="mt-4">
      <button
        class="text-sm font-semibold leading-6 py-3 px-7 text-white bg-blue-600 hover:bg-blue-800 transition ease-in-out duration-300 rounded-full"
        aria-label="Login"
        @click="handleSubmit"
      >
        {{submitType}}
      </button>
    </div>

    <!-- <ul class="form-list">
      <li class="form-item">
        <label class="label">Email</label>
        <div class="input-text-wrapper">
          <input
            type="email"
            name="email"
            class="input-text"
            placeholder="Email"
            required
          />
        </div>
      </li>
      <li class="form-item">
        <label class="label">Password</label>
        <div class="input-text-wrapper">
          <input
            type="password"
            name="password"
            class="input-text"
            placeholder="Password"
            required
          />
        </div>
      </li>
    </ul>
    <ul class="buttons-list u-margin-block-start-16">
      <li class="buttons-list-item">
        <button
          class="text-sm font-semibold leading-6 py-3 px-7 text-white bg-blue-600 hover:bg-blue-800 transition ease-in-out duration-300 rounded-full"
          aria-label="Login"
          @click="handleSubmit"
        >
          {{submitType}}
        </button>
      </li>
    </ul> -->
  </form>
</template>

<script setup>
import { defineProps } from 'vue'

const props = defineProps({
  handleSubmit: {
    type: Function,
    required: true
  },
  submitType: {
    type: String,
    required: true
  }
})
</script>
  