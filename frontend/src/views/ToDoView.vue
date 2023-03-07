<template>
  <div class="todos">
    <h1>This is the ToDos page</h1>
  </div>
  <div v-for="item in state.todos" :key="item.author" >
    <h2>
      {{ item.author }}
    </h2>
    <h4>
      {{ item.todo }}
    </h4>
    <p>
      {{ item.id }}
    </p>
  </div>
</template>

<script>
import { reactive, onMounted } from 'vue';

  export default{
    setup() {
      const state = reactive ({
        todos: {}
      })

      function GetAll() {
        fetch("http://localhost:3000/todos")
          .then(res => res.json())
          .then(data =>{
            state.todos= data
          })
      }
      onMounted(() => {
        GetAll()
      })
      return { state, GetAll}
    }
  }
</script>

<style>

</style>
