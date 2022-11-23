<template>
        <form class="form-wrapper" @submit.prevent="onSubmit">
        <div class="input-wrapper">
            <input
            v-model="text"
            placeholder="Please insert todo list" />
        </div>
        <p>Todo: {{text}}</p>
        <button type="submit">Insert Todo list</button>
    </form>

</template>
<script setup lang="ts">
import { ref } from 'vue';
    export interface ITodoList {
        id: number,
        title: string,
        date: Date,
    }
    const text = ref<string>();
    let id = 0;
    const emit = defineEmits(['submit-item']);
    function onSubmit(){
        if (!text.value){
            return;
        }
        emit('submit-item', {
            id,
            title: text.value,
            date: new Date()
        });
        id += 1;
        text.value = ''
    }
</script>
<style>
    .form-wrapper{
        display: flex;
        flex-direction: column;
    }
    .input-wrapper{
        padding: 4px 4px;
        overflow: hidden;

    }
    .input-wrapper input{
        width: 100%;
        height: 100%;
        outline: none;
        border: 0;
    }
</style>
