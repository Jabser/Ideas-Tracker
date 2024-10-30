<!-- pages/index.vue -->
<script setup>
const user = useUserSession();
</script>

<template>
  <div class="">
    <!-- Idea form component for logged in users -->
    <section v-if="user.current.value" class="border border-gray-900/10 rounded-lg p-6 mb-6">
      <IdeasForm />
    </section>

    <section v-else class="border border-gray-900/10 rounded-lg p-6 mb-6">
      <div class="container">
        <p>
          Please login to submit an idea.
        </p>
      </div>
    </section>
    <IdeasList class="border border-gray-900/10 rounded-lg p-6" />
  </div>
</template>
