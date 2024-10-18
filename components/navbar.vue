<template>
  <header class="bg-white border border-gray-900/10">
    <nav class="container mx-auto flex items-center justify-between py-6 px-1" aria-label="Global">
      <div class="flex lg:flex-1">
        <a href="/" class="text-gray-900 flex justify-start items-center">
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="h-8 w-auto size-6">
            <path stroke-linecap="round" stroke-linejoin="round" d="M12 18v-5.25m0 0a6.01 6.01 0 0 0 1.5-.189m-1.5.189a6.01 6.01 0 0 1-1.5-.189m3.75 7.478a12.06 12.06 0 0 1-4.5 0m3.75 2.383a14.406 14.406 0 0 1-3 0M14.25 18v-.192c0-.983.658-1.823 1.508-2.316a7.5 7.5 0 1 0-7.517 0c.85.493 1.509 1.333 1.509 2.316V18" />
          </svg>
          <h2 class="ml-4 text-lg font-semibold leading-6">Ideas Tracker</h2>
        </a>
      </div>
      <div class="hidden lg:flex lg:flex-1 lg:justify-end">
        <!-- Email and logout button if logged in user -->
        <div
          class="text-sm font-semibold leading-6 py-3 px-7 text-white bg-blue-600 hover:bg-blue-800 transition ease-in-out duration-300 rounded-full"
          v-if="user.current.value"
          >
          <p>{{ user.current.providerUid }}</p>
          <button class="button" type="button" @click="user.logout()">
            Logout
          </button>
        </div>
        <!-- Login button if no user logged in -->
        <NuxtLink v-else href="/login" class="text-sm font-semibold leading-6 py-3 px-7 text-white bg-blue-600 hover:bg-blue-800 transition ease-in-out duration-300 rounded-full">Log in</NuxtLink>
      </div>
    </nav>
  </header>
</template>

<script setup>
const user = useUserSession();
</script>