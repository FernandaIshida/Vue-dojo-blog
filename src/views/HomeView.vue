<template>
  <div class="home">
   <h1>Home</h1>
   <PostList v-if="showPosts" :posts="posts"/>
   <button @click="showPosts = !showPosts">toggle posts</button>
   <button @click="posts.pop()">delete a post</button>

  </div>
</template>

<script>
import PostList from '../components/PostList.vue'
import { ref } from 'vue'

export default {
  name: 'HomeView',
  components: { PostList },
  setup() {
    const posts = ref([
      {title: 'welcome to my blog', body: 'In sem justo, commodo ut, suscipit at, pharetra vitae, orci. Duis sapien nunc, commodo et, interdum suscipit, sollicitudin et, dolor. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Aliquam id dolor. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos. Mauris dictum facilisis augue. Fusce tellus. Pellentesque arcu. Maecenas fermentum, sem in pharetra pellentesque, velit turpis volutpat ante, in pharetra metus odio a lectus. Sed elit dui, pellentesque a, faucibus vel, interdum nec, diam. Mauris dolor felis, sagittis at, luctus sed, aliquam non, tellus. Etiam ligula pede, sagittis quis, interdum ultricies,', id: 1},
      {title: 'top 5 css tips', body: 'In sem justo, commodo', id: 2}
    ])
    const showPosts = ref(true)
    
    return { posts, showPosts }

  }
}
</script>
