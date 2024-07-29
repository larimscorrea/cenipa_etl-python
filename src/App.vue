<script setup>
import { ref, onMounted, computed, watch } from 'vue'

const todos = ref([])
const name = ref('')

const input_content = ref('')
const input_category = ref(null)

const todos_asc = computed(() => todos.value.sort((a, b) => {
  return a.createAt - b.createAt
}))

const addTodo = () => 

watch(name, (newVal) => {
  localStorage.setItem('name', newVal)
})

onMounted(() => {
  name.value = localStorage.getItem('name') || ``
})

</script>

<template>
    <main class="app">
      
      <section class="greeting">
        <h2 class="title">
          What's up, <input type="text" placeholder="Name here" v-model="name" />
        </h2>
      </section>

      <section class="create-todo">
        <h3>CREATE A TO DO</h3>
        
        <form @submit.prevent=""> 
          <h4>What's on your todo list?</h4>
          <input 
          type="text" 
          placeholder="e.g. make a video" 
          v-model="input_content" />

          <h4>Pick a category</h4>
        
          <div class="options">
            </div>
        </form>
      </section>
      
    </main>
</template>

<style>
/* Adicione seu código CSS aqui, se necessário */
</style>
