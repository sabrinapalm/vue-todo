<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
        <p class="title">
            <input type="checkbox" v-model="todo.completed" v-bind:id="todo.id" v-on:change="markComplete" />
            <label v-bind:for="todo.id"><span></span></label>
             {{todo.title}}
            <button @click="$emit('del-todo', todo.id)" class="del">🗑️</button>
        </p>
    </div>
</template>

<script>
export default {
    name: 'TodoItem',
    props: ['todo'],
    methods: {
        markComplete() {
         // this.todo.completed = !this.todo.completed
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
.del {
    background-color: transparent;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
    outline: none;
}

.title {
 font-size: 14px;
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
    background:url(https://s3-us-west-2.amazonaws.com/s.cdpn.io/210284/check_radio_sheet.png) left top no-repeat;
    cursor:pointer;
}

input[type="checkbox"]:checked + label span {
    background:url(https://s3-us-west-2.amazonaws.com/s.cdpn.io/210284/check_radio_sheet.png) -19px top no-repeat;
}
</style>