<script setup>
import { reactive, ref } from 'vue';
import HeaderCompenent from './HeaderCompenent.vue';
import TodoList from './TodoList.vue';

const props = defineProps({
    setCounter: Function
})
const todoList = reactive([])
const isCheckAll = ref(false)
const id = ref(0)

const header = ref(null)

const addTodoList = (text) => {
    const todo = { id: id.value++, title: text, isCompleted: false }
    todoList.push(todo);
    header.value.clearText();
    props.setCounter(todoList.length)

}

const compleTask = (id) => {
    const todo = todoList.find(todo => todo.id === id);
    todo.isCompleted = !todo.isCompleted;
}

const deleteTask = (id) => {
    const todoIndex = todoList.findIndex(todo => todo.id === id);
    todoList.splice(todoIndex, 1);
    props.setCounter(todoList.length)
}

const compleAll = () => {
    isCheckAll.value = !isCheckAll.value
    todoList.forEach(todo => { todo.isCompleted = isCheckAll.value })
}

</script>

<template>
    <div class="main">
        <HeaderCompenent :addTodoList="addTodoList" ref="header" />
        <TodoList :todoList="todoList" :compleTask="compleTask" :deleteTask="deleteTask" :compleAll="compleAll" />
    </div>
</template>
<style scoped>
.main {
    width: 50%;
}
</style>