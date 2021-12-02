<template>
  <article class="grid grid-cols-12 pt-6 pb-24">
    <nuxt-img
      class="w-full col-span-8 col-start-3 rounded-lg"
      :src="post.image"
      width="768"
      height="409"
    />

    <div class="grid w-full grid-cols-12 col-span-12 col-start-1">
      <nav class="self-start col-span-2 p-4 mt-8 rounded-lg shadow-2xl">
        <ul class="space-y-2">
          <li v-for="link of post.toc" :key="link.id">
            <NuxtLink
              class="tracking-wider text-gray-500 uppercase hover:underline"
              :to="`#${link.id}`"
              >{{ link.text }}</NuxtLink
            >
            >
          </li>
        </ul>
      </nav>
      <div class="w-full col-span-6 col-start-4">
        <div>
          <ul v-if="post.tags" class="flex mt-2 space-x-3">
            <li
              v-for="tag in post.tags"
              :key="tag"
              class="font-bold text-gray-400"
            >
              {{ tag }}
            </li>
          </ul>
          <h1 class="mt-2 text-5xl font-black">{{ post.title }}</h1>
        </div>
        <nuxt-content class="mt-4 prose max-w-none" :document="post" />
      </div>
    </div>
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const post = await $content(params.slug).fetch()
    return { post }
  },
}
</script>
