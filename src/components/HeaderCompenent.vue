<script setup>
import { ref, reactive, watch } from 'vue'
const text = ref('')
const count = ref(0)

</script>
<template>
    <div class="header">
        <input v-model="text" />
        <button>Submit</button>
    </div>
    <h3 @click="count++"> hallo{{ text }} - {{ count }}</h3>
</template>
<style scoped>
.header {
    display: flex;
    width: 500px;
}

.header input {
    flex-grow: 1;
    border-radius: 5px;
}
</style>