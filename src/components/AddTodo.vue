<template>
 <div>
  <form @submit="addTodo">
   <input type="text" v-model="title" name="title" placeholder="Add todo..">
   <input type="submit" name="Submit" class="btn" value="Add">
  </form>
 </div>
</template>

<script>
// import uuid from 'uuid';
export default {
 name: "AddTodo",
 data() {
  return {
   title: ''
  }
 },
 methods: {
  addTodo(e) {
   e.preventDefault();
   const newTodo = {
    title: this.title,
    completed: false
   }
   if(newTodo.title) {
    this.$emit('add-todo', newTodo);
    this.title = '';
   } else {
    console.log('input field is empty..');   
   }
  }
 }
}
</script>


<style scoped>
form {
 display: flex;
}

input[type="text"] {
 flex: 10;
 padding: 5px;
 font-size: 14px;
 outline: none;
}

input[type="submit"] {
 flex: 1;
 outline: none;
 font-size: 13px;
}

</style>