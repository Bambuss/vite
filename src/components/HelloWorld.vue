<script setup>
import { ref, onMounted } from 'vue'
import axios from "axios"

defineProps({
  msg: String
})


const items = ref([])
onMounted(()=> {
  axios.get('https://jsonplaceholder.typicode.com/todos').then(res => {
    items.value = res.data;
  })
})



const count = ref(0)
</script>

<template>
  <h1>{{ msg }}</h1>

  <div v-for="item in items" :key="item.id">
    {{item.title}}
  </div>

 
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
