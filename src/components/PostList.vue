<template>
  <div v-if="posts.length > 0">
    <h3>Список постов</h3>
    <transition-group name="postList">
      <post-item :post="post"
                 v-for="post in posts"
                 :key="post.id"
                 @remove="$emit('remove', post)"
      />
    </transition-group>

  </div>
  <h2 v-else style="color: red">список постов пуст</h2>
</template>

<script>
import PostItem from "@/components/PostItem";
export default {
  name: "PostList",
  components: {
    PostItem
  },
  data() {

  },
  props: {
    posts: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>
.postList-item {
  display: inline-block;
  margin-right: 10px;
}
.postList-enter-active,
.postList-leave-active {
  transition: all 0.4s ease;
}
.postList-enter-from,
.postList-leave-to {
  opacity: 0;
  transform: translateX(130px);
}
.postList-move {
  transition: transform 0.4s ease;
}
</style>