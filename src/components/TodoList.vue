<script setup>
import { defineProps, watch } from 'vue'
const props = defineProps({
    todoList: Array,
    compleTask: Function,
    deleteTask: Function,
    compleAll: Function
})

const onCompledChange = (id) => {
    props.compleTask(id)
}

const onDeleteTask = (id) => {
    props.deleteTask(id)
}

const onCompledAllChange = () => {
    props.compleAll()
}
</script>
<template>
    <div class="todo-list">
        <table class="table">
            <tr>
                <th><input type="checkbox" @change="onCompledAllChange" />All</th>
                <th class="center">Tasks</th>
                <th class="center">Action</th>
            </tr>
            <tr v-for="todo in props.todoList">
                <td><input type="checkbox" :checked="todo.isCompleted" @change="onCompledChange(todo.id)" /></td>
                <td :class="[{ done: todo.isCompleted }]">{{ todo.title }}</td>
                <td class="center"><button class="btn btn-danger" @click="onDeleteTask(todo.id)">Delete</button></td>
            </tr>
        </table>
    </div>


</template>
<style scoped>
.todo-list {
    margin-top: 10px;
    border: 1px solid #CCC;
    min-height: 100px;
    min-width: 500px;
    border-radius: 4px;
    padding: 10px;
}

.todo-list .table {
    width: 100%;
    text-align: left;
    border-collapse: collapse;
}

.todo-list .table td,
.todo-list .table th {
    border: 1px solid black;
    padding: 2px 5px;
}

.todo-list .table td:first-child,
.todo-list .table td:last-child {
    width: 15%;
}

.todo-list .line {
    display: flex;
    align-items: center;
    text-align: left;
}

.todo-list .message {
    display: inline-block;
    flex-grow: 1;
    margin-left: 5px;
}

.todo-list li button {
    float: right;
}

.center {
    text-align: center;
}

.todo-list .done {
    text-decoration: line-through;
    color: #CCC;
}
</style>