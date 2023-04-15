<script>
export default {
  name: 'postList',
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
  methods: {
    dateParser(props) {
      const date = new Date(props)
      const options = {
        day: '2-digit',
        month: '2-digit',
        year: 'numeric',
      }
      return date.toLocaleDateString('cs-CZ', options)
    },
  },
}
</script>

<template>
  <section class="container d-flex flex-column gap-3 align-items-center">
    <article
      class="card"
      v-for="item in items"
      :key="item.id"
      style="width: 50rem; height: 35rem"
    >
      <img
        class="card-img-top img-fluid"
        :src="item.image"
        style="overflow: hidden; object-fit: cover"
      />
      <div class="card-body">
        <h4 class="card-title">{{ item.title }}</h4>
        <p class="card-text">{{ item.content }}</p>
        <footer class="d-flex flex-row justify-content-between">
          <p class="card-text text-body-secondary">
            {{ dateParser(item.createdAt) }}
          </p>
          <NuxtLink class="btn btn-primary btn-outline" :to="`${item.id}`">
            Přejít na článek
          </NuxtLink>
        </footer>
      </div>
    </article>
  </section>
</template>
