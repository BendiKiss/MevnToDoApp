<template>
   <h1>All todos</h1>
  <button @click="newTodo()">New To Do</button>
  <br>
  <input type="text" placeholder="Author" v-model="state.newAuthor">
    <span> Test: {{ state.newAuthor }}</span>
  <input type="text" placeholder="ToDos" v-model="state.newToDos">
    <span> Test: {{ state.newToDos }}</span>

  <br>
  
  <div v-for="item in state.todos" :key="item._id" >
     <RouterLink :to="`/todo/${item._id}`">
      <h3>
        {{ item.author }}
      </h3>
      <h4>
        {{ item.todo }}
      </h4>

      <button @click="editTodo(item._id)">Edit To Do</button>
    </RouterLink>
    <button @click="deleteTodo(item._id)">Delete To Do</button>
     

  </div>
</template>

<script setup>
  import todocrud from '../moduls/todocrud';
  import { onMounted } from 'vue';
  import { RouterLink } from 'vue-router';



      const { state, GetAllTodos, newTodo, deleteTodo, editTodo } = todocrud()

      onMounted(() => {
        GetAllTodos()
      })

return { state, GetAllTodos, newTodo, deleteTodo, editTodo }

</script>

<style>

</style>
