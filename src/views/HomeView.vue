<template>
  <div class="home">
   <h1>Home</h1>
   <input type="text" v-model="search">
   <p>Search term - {{ search }}</p>
   <div v-for="name in matchingNames" :key="name">{{ name }}</div>
   
  </div>
</template>

<script>
import { computed, ref } from 'vue'

export default {
  name: 'HomeView',
  setup() {
    const search = ref('')
    const names = ref(['mario', 'yoshi', 'luigi', 'toad', 'bowser', 'koopa', 'peach'])

    // This computed property returns updated value based on other values (in this case, const names array)
    const matchingNames = computed(() => {
      return names.value.filter((name) => name.includes(search.value))
    })
    
    return { names, search, matchingNames }

  }
}
</script>
