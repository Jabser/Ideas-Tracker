<script setup>
import { ref } from 'vue';

// Access user composable functions
const user = useUserSession();

const isSignUp = ref(false);

// Login user event handler
const handleLogin = async (event) => {
  const form = event.target;
  const formData = new FormData(form);

  await user.login(formData.get('email'), formData.get('password'));

  form.reset(); // Clear the form
};

const handleRegistration = async (event) => {
  const form = event.target;
  const formData = new FormData(form);

  await user.register(formData.get('email'), formData.get('password'));

  form.reset(); // Clear the form
};
</script>

<template>
  <div class="contaier border border-gray-900/10 rounded-lg p-6 px-6 space-y-4">
    <h2 class="text-5xl font-semibold mb-4">Login/Register</h2>
    <AuthForm v-if="isSignUp" :handle-submit="handleRegistration" submit-type="Sign Up"></AuthForm>
    <AuthForm v-else :handle-submit="handleLogin" submit-type="Log In"></AuthForm>
    <button v-if="isSignUp" @click="isSignUp = false" class="underline underline-offset-2 hover:text-blue-800 transition ease-in-out duration-300">
      Already have an account? Log in
    </button>
    <button v-else @click="isSignUp = true" class="underline underline-offset-2 hover:text-blue-800 transition ease-in-out duration-300">
      Don't have an account? Sign up
    </button>
  </div>
</template>
