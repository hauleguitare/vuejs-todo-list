<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import { ref } from 'vue';
import FormInput, { ITodoList } from './components/form-input/FormInput.vue'
import ListTodo from './components/list-todo/ListTodo.vue'


const listTodo = ref<ITodoList[]>([]);

function handleSubmit(value: any){
    console.log(value);
    listTodo.value.push(value);
}

function handleRemove(item_id: number){
    const findIdx = listTodo.value.findIndex((value) => value.id === item_id);
    if (findIdx === -1){
        return;
    }
    listTodo.value.splice(findIdx, 1);
}
</script>

<template>
  <div>
    <p class="title-list">TODO LIST with VueJS</p>
    <FormInput @submit-item="handleSubmit"/>
    <ListTodo :data="listTodo" @remove-item="handleRemove"/>


  </div>
</template>

<style scoped>
.title-list {
    font-size: 30px
}

.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
