<template>
  <div>
    <router-link to='/'>back to home</router-link>
    <AddTodo 
      @add-todo="addTodo"
    />
    <select v-model="filter"  >
      <option selected value="all">all</option>
      <option value="completed">completed</option>
      <option value="not-completed">not completed</option>
    </select>
    
    <TodoList
      v-if="filterTodos.length"
      v-bind:todos="filterTodos"
      @remove-todo = "removeTodo"
    />
    <p v-else>нет дел</p>
  </div>
</template>
 
<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'

export default {
  name: 'Todos',
  data(){
    return {
      todos: [],
      filter :'all'
    }
  },
  computed: {
    filterTodos(){
      if(this.filter === 'all'){
        return this.todos
      }
      else if (this.filter === 'completed'){
        return this.todos.filter(todo => todo.completed);
      }
      else if (this.filter === 'not-completed'){
        return this.todos.filter(todo => !todo.completed);
      }
      return true;
      // switch(this.filter){
      //   case 'all': 
      //     return this.todos;

      //   case 'completed':
      //     return this.todos.filter(todo => todo.completed);

      //   case 'not-completed':
      //     return this.todos.filter(todo => !todo.completed);

      //   default :
      //     return this.todos;
      // }
    }
  },
  methods:{
    removeTodo(id){
      this.todos = this.todos.filter(todo => todo.id !== id)
    },
    addTodo(todo){
      this.todos.push(todo)
    }
  },
  components: {
    TodoList: TodoList,
    AddTodo: AddTodo
  }
}
</script>

<style scoped>
  select{
    outline: none;
    border: 1px solid #ccc;
    border-radius: 5px;
    margin-bottom: 10px;
  }
</style>