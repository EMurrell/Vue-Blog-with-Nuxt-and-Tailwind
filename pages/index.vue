<template>
  <div>
    <h1 class="text-6xl font-semibold text-center pt-20">
      A Blog Built with Vue.js and TailwindCSS
    </h1>

    <ul class="grid grid-cols-3 gap-8 mt-20">
      <PostPreview
        v-for="post in posts"
        :key="post.slug"
        :post="post"
      ></PostPreview>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const posts = await $content()
      .only(['title', 'image', 'tags', 'slug'])

      .sortBy('createdAt', 'desc')

      .fetch()

    return {
      posts,
    }
  },
}
</script>
