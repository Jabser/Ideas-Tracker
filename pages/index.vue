<!-- pages/index.vue -->
<script setup>
const user = useUserSession();
</script>

<template>
  <div>
    <!-- Idea form component for logged in users -->
    <section v-if="user.current.value" class="border border-gray-900/10 rounded-lg p-6 mb-6">
      <IdeasForm />
    </section>

    <section v-else class="border border-gray-900/10 rounded-lg p-6 mb-6">
      <div class="container">
        <p>
          Please <NuxtLink href="/login" class="underline underline-offset-2 font-bold hover:text-blue-800 transition ease-in-out duration-300">login</NuxtLink> to submit an idea.
        </p>
      </div>
    </section>
    <IdeasList class="border border-gray-900/10 rounded-lg p-6" />
  </div>
</template>
