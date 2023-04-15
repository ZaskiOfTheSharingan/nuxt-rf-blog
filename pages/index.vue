<script>
export default {
  name: 'HomePage',
  layout: 'default',
  data() {
    return {
      items: [],
    }
  },
  async fetch() {
    const response = await this.$axios.$get(
      'https://62fe137ba85c52ee482f275b.mockapi.io/api/v1/posts'
    )
    this.items = response
  },
}
</script>

<template>
  <div>
    <postList />
  </div>
</template>
