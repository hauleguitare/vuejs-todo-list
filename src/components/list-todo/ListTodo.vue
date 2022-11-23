<template>
    <ul v-if="props.data">
        <li v-for="item of props.data" :key="item.id">
            <button @click.left="onRemove(item.id)">
                <span>
                    {{item.title}}
                </span>
            </button>
        </li>
    </ul>
</template>
<script setup lang="ts">
import { ITodoList } from '../form-input/FormInput.vue';

    export interface IListTodoProps{
        data?: ITodoList[]
    }
    const props = withDefaults(defineProps<IListTodoProps>(), {});
    const emit = defineEmits(['remove-item']);

    function onRemove(item_id: number){
        emit('remove-item', item_id);
    }

</script>
<!-- <style scoped>
    .finish-todo {
        text-decoration: line-through;
        font-style: italic;
    }
</style> -->
