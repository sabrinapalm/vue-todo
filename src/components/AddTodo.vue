<template>
 <div>
  <form @submit="addTodo">
   <input type="text" v-model="title" name="title" placeholder="Add todo..">
   <button type="submit" name="Submit">
    <img src="../assets/plus.svg"/>
   </button>
  </form>
 </div>
</template>

<script>
export default {
 name: "AddTodo",
 data() {
  return {
   title: '',
   completed: false,
   date: Date()
  }
 },
 methods: {
  addTodo(e) {
   e.preventDefault();

   const newTodo = {
    title: this.title,
    completed: false,
    date: Date()
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
 padding: 10px;
 font-size: 14px;
 outline: none;
 border:none;
}

input[type="text"]:focus {
    outline:none;
}



button[type="submit"] {
 background-color: transparent;
 -webkit-box-flex: 1;
 padding: 7px;
 width: 41px;
 outline: none;
 border:none;
}

button[type="submit"]:focus {
 outline:0;
}

button[type="submit"]:active {
  transform: translateY(1px);
}



</style>