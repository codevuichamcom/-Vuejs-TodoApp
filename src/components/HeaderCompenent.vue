<script setup>
import { ref, defineProps } from 'vue'
const props = defineProps({
    addTodoList: Function,
})
const text = ref('')

const onSubmit = () => {
    if (text.value)
        props.addTodoList(text.value)
}

const clearText = () => {
    text.value = ''
}


defineExpose({ clearText })


</script>
<template>
    <div class="header">
        <input v-model="text" @keyup.enter="onSubmit" />
        <button class="btn btn-primary" @click="onSubmit">Submit</button>
    </div>
</template>
<style scoped>
.header {
    display: flex;
    width: 500px;
}

.header input {
    flex-grow: 1;
    margin: 0 10px 0 10px;
    border-radius: 5px;
    padding: 5px 10px;
    border: 2px solid black
}
</style>