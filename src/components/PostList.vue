<template>
  <div v-if="posts.length > 0">
    <h3>Список заметок</h3>
    <transition-group name="post-list">
    <post-item
        v-for="post in posts"
        :post="post"
        :key="post.id"
        @remove="$emit('remove', post)"
    />
    </transition-group>
  </div>
<div v-else>
  <h3 class="alert">
    Список заметок пуст
  </h3>
</div>

</template>

<script>
import PostItem from "@/components/PostItem";
export default {
  components: {PostItem},
  props: {
    posts: {
      type: Array,
      required: true,
    }
  }
}
</script>

<style scoped>
.alert {
  color:teal;
  text-align: left;
  margin: 10px 0;
}

.post-list-item {
  display: inline-block;
  margin-right: 10px;
}
.post-list-enter-active,
.post-list-leave-active {
  transition: all 0.5s ease;
}
.post-list-enter-from,
.post-list-leave-to {
  opacity: 0;
  transform: translateX(200px);
}

.post-list-move {
  transition: transform 0.8s ease;
}
</style>