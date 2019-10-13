<template>
    <div id="app">
        <Header />
        <AddTodo v-on:add-todo="addTodo" />
        <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    </div>
</template>

<script>
import Header from './components/layout/Header'
import Todos from './components/Todos'
import AddTodo from './components/AddTodo'
import axios from 'axios';


export default {
    name: 'app',
    components: {
        Header,
        Todos,
        AddTodo,
    },
    data() {
        return {
            todos: [],
        }
    },
    methods: {
        deleteTodo(_id) {
            let url = `https://vue-todo-api.herokuapp.com/todos/${_id}`;
            axios.delete(url)
            .then(res => this.todos = this.todos.filter(todo => todo._id !== _id))
            .catch(err => console.log(err))
        },
        addTodo(newTodo) {
            let url = 'https://vue-todo-api.herokuapp.com/todos';
            axios.post(url, newTodo)
            .then(res => this.todos = [...this.todos, res.data])
            .catch(err => console.log(err));
        }
    },
    created() {
        let url = 'https://vue-todo-api.herokuapp.com/todos';
        axios.get(url).then(res => {
         this.todos = res.data
        })
        .catch(err => console.log(err));
    }
}
</script>

<style>
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
}

input, textarea, select, a { outline: none;  }

.btn {
    display: inline-block;
    border: none;
    background: transparent;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
}
</style>
