<template>
  <form @submit.prevent="onSubmit" action="">
    <input type="text" v-model="title">
    <button >добавить</button>
  </form>
</template>

<script>
export default {
  data(){
    return {
      title: ''
    }
  },
  methods: {
    onSubmit(){
      if(this.title.trim()){
        const newTodo = {
          id:Date.now(),
          title: this.title,
          completed: false
        }
        this.$emit('add-todo',newTodo)
        this.title = ''
      }
    }
  }
}
</script>

<style scoped>
  form{
    margin: 10px 0;
  }
  input{
    border: none;
    outline: none;
    border-bottom: 1px solid black;
    margin-right: 10px;
    padding: 5px;

  }
  button{
    outline: none;
    border: none;
    padding: 5px;
    background-color: rgb(146, 219, 103);
    border-radius: 5px;
    color: white;
    cursor: pointer;
    transition: .2s ease;
  }
  button:hover{
    background-color: rgb(112, 175, 76);
  }
</style>