<script setup>
import { ref } from 'vue'
const count = ref(0)
const increaseCount = () => {
    count.value++;
}
</script>
<template>
    <div class="todo-list">
        <div>
            <div class="line" @click="increaseCount"> - <span class="message">Go to
                    school {{ count }}</span><button>Edit</button><button>Delete</button>
            </div>
        </div>


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
</style>