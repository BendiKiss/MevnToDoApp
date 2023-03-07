<template>
  <div v-for="item in state.todos" :key="item.id" >
    <p>
      {{ item._id }}
    </p>
    <h3>
      {{ item.author }}
    </h3>
    <h4>
      {{ item.todo }}
    </h4>
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
