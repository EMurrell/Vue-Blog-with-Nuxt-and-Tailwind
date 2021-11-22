<template>
  <h1>{{ post.title }}</h1>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const post = await $content(params.slug).fetch()
    return { post }
  },
}
</script>
