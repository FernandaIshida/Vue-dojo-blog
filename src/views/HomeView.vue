<template>
  <div class="home">
   Home
   <p ref="p">My name is {{ name }} and my age is {{ age }}</p>
   <button @click="handleClick">Click me</button>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  name: 'HomeView',
  setup() {
    console.log(this)

    const p = ref(null)
    console.log(p, p.value)

    let name = 'mario'
    let age = 30

    const handleClick = () => {
      console.log(p, p.value)
      p.value.classList.add('test')
      p.value.textContent = 'Hello, ninjas'
    }

    return { name, age, handleClick, p }
  }
}
</script>
