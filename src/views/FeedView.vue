<template>
  <div>
    <h1>Mini Feed</h1>

    <PostCard
      v-for="post in posts"
      :key="post.id"
      :author="post.author"
      :created="post.created"
      :id="post.id"
      :text="post.text"
    />
  </div>
</template>

<script>
import PostCard from "@/components/PostCard.vue";

export default {
  components: {
    PostCard,
  },
  data() {
    return {
      posts: [],
    };
  },
  mounted() {
    this.$axios
      .get("/posts/")
      .then((response) => (this.posts = response.data.posts))
      .catch((error) => console.error(error.message));
  },
};
</script>

<style lang="scss" scoped></style>
