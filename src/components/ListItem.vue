<template>
    <li>
        <input 
            type="checkbox" 
            class="input-checkbox"
            :checked="todo.done"
            @click="doneTodo(index)"
        />
        <input 
            type="text" 
            class="input-list"  
            autocomplete="off"
            :value="todo.content"
            :class="{ done: todo.done }"
            @input="saveNewInput($event, index)"  
        />
        <button 
            class="button-remove"
            @click="removeTodo(index)"
        >&#10006;</button>
    </li>
</template>

<script>
export default {
    props: ['todo', 'index'],
    emits: ['doneTodo', 'saveNewInput', 'removeTodo'],
    setup(props, { emit }) {
        function doneTodo(index) {
            emit('doneTodo', index);
        }

        function saveNewInput(event, index) {
            emit('saveNewInput', event.target.value, index);
        }

        function removeTodo(index) {
            emit('removeTodo', index);
        }

        return {
            doneTodo,
            saveNewInput,
            removeTodo
        };
    },
}
</script>