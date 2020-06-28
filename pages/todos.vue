<template>
  <div>
    <!-- {{ todos }} -->
    <ul>
      <li v-for="todo in todos" :key="todo.id">
        <!-- {{ todo }}; -->
        {{ todo.done }}, {{ todo.name }}, {{ todo.created }}
      </li>
    </ul>
    <div class="form">
      <form @submit.prevent="add">
        <input v-model="name">
        <button>ADD</button>
      </form>
    </div>

  </div>
</template>

<script>
  export default {
    data(){
      return {
        name: '',
        done: false
      }
    },
    created() {
      this.$store.dispatch('todos/init')
    },
    methods: {
      add(){
        this.$store.dispatch('todos/add', this.name)
        this.name = ''
      }
    },
    computed: {
      todos(){
        return this.$store.state.todos.todos
      }

    }
  }
</script>
