<template>
  <form @submit.prevent>
    <h4>Создание поста</h4>

    <my-input v-model="post.title" placeholder="Название"/>
    <my-input v-model="post.body" placeholder="Описние"/>
    <my-button
        class="btn"
        style="align-self: flex-end; margin-top: 15px;"
        @click="createPost"
    >
      создание поста
    </my-button>

  </form>
</template>

<script>

export default {
  name: "PostForm",
  data() {
    return {
      post: {
        title: '',
        body: ''
      }
    }
  },
  methods: {
    createPost() {
      this.post.id = Date.now()
      this.$emit('create', this.post)
      this.post = {
        title: '',
        body: ''
      }

    }
  }
}
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}
</style>