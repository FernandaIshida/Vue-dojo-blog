<template>
  <div class="home">
   <h1>Home</h1>
   <input type="text" v-model="search">
   <p>Search term - {{ search }}</p>
   <div v-for="name in matchingNames" :key="name">{{ name }}</div>
   <button @click="handleClick">stop watching</button>
   
  </div>
</template>

<script>
import { computed, ref, watch, watchEffect } from 'vue'

export default {
  name: 'HomeView',
  setup() {
    const search = ref('')
    const names = ref(['mario', 'yoshi', 'luigi', 'toad', 'bowser', 'koopa', 'peach'])

    //This function doesn't run initialy when the componet first runs
    //If you dont use a value inside the function this the best option
    const stopWatch = watch(search, () => {
      console.log('watch function ran')
    })

    //This function runs initialy when the componet first runs
    //Use this function if you want to use a value inside the function
    const stopEffect = watchEffect(() => {
      console.log('watchEffectt function ran', search.value)  
    })

    // This computed property returns updated value based on other values (in this case, const names array)
    const matchingNames = computed(() => {
      return names.value.filter((name) => name.includes(search.value))
    })

    const handleClick = () => {
      stopWatch()
      stopEffect()
    }
    
    return { names, search, matchingNames, handleClick }

  }
}
</script>
