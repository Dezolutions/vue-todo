<template>
  <li >
    <input type="checkbox" v-model="todo.completed">
    <p 
      v-bind:class="{done: todo.completed}"
      v-on:click="todo.completed = !todo.completed"
    >
      <strong>{{index +1}}</strong>
      {{todo.title}}
    </p>
    <button v-on:click="$emit('remove-todo',todo.id)">&times;</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      requiered: true
    },
    index: Number
  }
}
</script>

<style scoped>
p{
  margin: 5px 0;
}
 .done{
   text-decoration: line-through;
 }
 li{
   display: flex;
   align-items: center;
   justify-content: center;
   cursor: pointer;
 }
 button{
   outline: none;
   border: none;
   background-color: transparent;
   color: red;
   border-radius: 5px;
   margin-left: 5px;
   cursor: pointer;
   transition: .2s ease;
 }
 button:hover{
   
   background-color: rgb(255, 213, 213);
 }
</style>