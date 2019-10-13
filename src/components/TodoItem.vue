<template>
    <div class="todo-item">
        <p class="title" v-bind:class="{'is-complete':todo.completed}">
            <input type="checkbox" v-model="todo.completed" v-bind:id="todo._id" v-on:change="markComplete(todo._id, todo.completed)"/>
            <label v-bind:for="todo._id"><span></span></label>
             {{todo.title}}
            <button @click="$emit('del-todo', todo._id)" class="del">🗑️</button>
        </p>
        <span class="date-time">{{(new Date(todo.date).toISOString().substring(0, 10))}}</span>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'TodoItem',
    props: ['todo'],
    methods: {
        markComplete(_id, completed) {
            let url = `https://vue-todo-api.herokuapp.com/todos/${_id}`;
            axios.patch(url, { completed })
            .then(res => console.log(res))
            .catch(err => console.log(err))
        }
    }
}
</script>

<style scoped>
.todo-item {
    background-color: #fbfbfb;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
}
.is-complete {
    text-decoration: line-through;
}

.date-time {
    font-size: 11px;
    color: #9a9a9a;
}
.del {
    background-color: transparent;
    color: #fff;
    border: none;
    padding: 5px 2px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
    outline: none;
}

.title {
 font-size: 14px;
 color: #34373d;
}

input[type="checkbox"] {
    display:none;
}

input[type="checkbox"] + label {
    color:#f2f2f2;
}

input[type="checkbox"] + label span {
    display:inline-block;
    width:19px;
    height:19px;
    margin:-2px 10px 0 0;
    vertical-align:middle;
    background:url(../assets/check_radio_sheet.png) left top no-repeat;
    cursor:pointer;
}

input[type="checkbox"]:checked + label span {
    background:url(../assets/check_radio_sheet.png) -19px top no-repeat;
}
</style>