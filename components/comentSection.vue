<script>
export default {
  name: 'commentSection',
  layout: 'default',
  data() {
    return {
      comments: [],
    }
  },
  async fetch() {
    const response = await this.$axios.$get(
      'https://62fe137ba85c52ee482f275b.mockapi.io/api/v1/comments'
    )
    this.comments = response
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

<script setup>
import { ref } from 'vue'

const name = ref('')
const comment = ref('')

const addComment = () => {
  if (name == null || comment == null) {
    return
  } else {
    $axios
      .post(
        `https://62fe137ba85c52ee482f275b.mockapi.io/api/v1/comments?name=${name}&comment=${comment}`
      )
      .then((res) => console.log(res))
      .catch((err) => console.log(err))
  }
}
</script>

<template>
  <section class="container d-flex flex-column gap-3 align-items-start gap-2">
    <form class="d-flex flex-column gap-2 w-100" @submit.prevent="addComment">
      <div>
        <input type="text" placeholder="Vaše jméno" v-model="name" />
      </div>
      <textarea placeholder="Váš komentář" v-model="comment"></textarea>
      <button class="btn btn-outline-primary">Přidat komentář</button>
    </form>
    <article
      v-for="comment in comments"
      class="align-content-start w-100 p-2 gap-1"
    >
      <div class="d-flex flex-row align-content-center gap-4">
        <img :src="comment.avatar" class="avatar" />
        <p>{{ comment.name }}</p>
        <p>{{ dateParser(comment.createdAt) }}</p>
      </div>
      <p>{{ comment.comment }}</p>
    </article>
  </section>
</template>

<style scoped>
form {
  border: solid 1px gainsboro;
  border-radius: 10px;
  padding: 10px;
}

textarea {
  resize: none;
  width: 100%;
}

p {
  margin: 0;
  align-self: center;
}

.avatar {
  border: solid 1px gainsboro;
  border-radius: 9999px;
  width: 50px;
  height: 50px;
}

article {
  border-radius: 10px;
}

article:hover {
  background-color: gainsboro;
  transition-duration: 0.35s;
}
</style>
