<script setup>
const ideas = useIdeas();
const user = useUserSession();

const handleAddIdea = async (event) => {
  const form = event.target;
  const formData = new FormData(form);

  // Extract the values from the FormData object and add userId
  const postIdeaData = {
    userId: user.current.value.userId,
    title: formData.get('title'),
    description: formData.get('description'),
  };

  await ideas.add(postIdeaData);

  form.reset(); // Clear the form
};
</script>

<template>
  <div>
    <article class="container">
      <h4 class="text-5xl font-semibold mb-4">Submit Idea</h4>
      <div class="lg:col-span-3">
        <form @submit.prevent="handleAddIdea" class="space-y-4">
          <div>
            <label class="sr-only" for="name">Title</label>
            <input
              class="w-full rounded-lg border border-gray-900/10 p-3"
              placeholder="Title"
              name="title"
              type="text"
              id="title"
            />
          </div>

          <div>
            <label class="sr-only" for="message">Description</label>

            <textarea
              class="w-full rounded-lg border border-gray-900/10 p-3"
              placeholder="Description"
              name="description"
              rows="8"
              id="description"
            ></textarea>
          </div>

          <div class="mt-4">
            <button
              type="submit"
              class="text-sm font-semibold leading-6 py-3 px-7 text-white bg-blue-600 hover:bg-blue-800 transition ease-in-out duration-300 rounded-full"
            >
              Submit Idea
            </button>
          </div>
        </form>
      </div>
    </article>
  </div>
</template>
