<template>
  <div>
    <section>
      <h1>{{ item.title }}</h1>
      <img
        class="figure-img img-fluid"
        :src="item.image"
        style="overflow: hidden; object-fit: cover"
      />
      <p>{{ item.content }}</p>
    </section>
    <section>
      <comentSection />
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      item: {},
    }
  },
  async asyncData({ params }) {
    const item = await fetch(
      `https://62fe137ba85c52ee482f275b.mockapi.io/api/v1/posts/${params.slug}`
      //`https://62fe137ba85c52ee482f275b.mockapi.io/api/v1/posts?search=${params.slug}` - filtrace díky query
    )
      .then((res) => res.json())
      .then((data) => {
        return data
        // return data.find((item) => params.slug == item.slug) - ošetření
      })
      .catch((err) => console.log(err))
    return {
      item,
    }
  },
}
</script>
