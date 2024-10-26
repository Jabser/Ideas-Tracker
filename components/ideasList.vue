<script setup>
import { onMounted } from 'vue';

const ideas = useIdeas();
const user = useUserSession();

import { TrashIcon } from '@heroicons/vue/24/outline'
</script>

<template>
  <section>
    <article>
      <h4 class="text-6xl font-semibold mb-4">Latest Ideas</h4>
      <ul>
        <template v-if="ideas.current.value && ideas.current.value.length">
          <li class="my-6 py-6 border border-b-0 border-x-0 border-t-1" v-for="idea in ideas.current.value">
            <div>
              <h5 class="text-3xl font-semibold mb-2">{{ idea.title }}</h5>
              <p class="">{{ idea.description }}</p>
              <div class="mt-6">
                <button class="text-sm font-semibold leading-6 py-3 px-7 text-white bg-red-600 hover:bg-red-800 transition ease-in-out duration-300 rounded-full" aria-label="Remove item" v-if="user.current.value &&
                  idea.userId === user.current.value.userId
                  " type="button" @click="ideas.remove(idea.$id)">
                  <span aria-hidden="true" class="flex justify-center items-center">
                    <TrashIcon class="size-5 mr-2" /> 
                    Delete
                  </span>
                </button>
              </div>
            </div>
          </li>
        </template>
        <template v-else>
          <p>No ideas yet.</p>
        </template>
      </ul>
    </article>
  </section>
</template>
