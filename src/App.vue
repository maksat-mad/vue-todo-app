<template>
  <div>
    <h1>ToDo App</h1>
    <form @submit.prevent="addTodo">
      <label>New ToDo List</label>
      <input 
        type="text" 
        name="newTodo" 
        placeholder="I will do..."
        autocomplete="off" 
        v-model.trim="newTodo"
      />
      <button class="button-add">Add ToDo</button>
    </form>
    <h2>ToDo List</h2>
    <ul>
      <ListItem
        v-for="(todo, index) in todos" 
        :key="index"
        :index="index"
        :todo="todo"
        @doneTodo="doneTodo"
        @saveNewInput="saveNewInput"
        @removeTodo="removeTodo"
      />
    </ul>
    <h3 v-if="todos.length === 0" class="no-item-text">Empty list</h3>
  </div>
</template>

<script>
import { ref } from 'vue';
import ListItem from './components/ListItem.vue';

export default {
  name: "App",
  components: {
    ListItem
  },
  setup() {
    const newTodo = ref('');
    const defaultData = [{
      done: false,
      content: 'Do math'
    }];

    const todoData = JSON.parse(localStorage.getItem('todos')) || defaultData;
    const todos = ref(todoData);

    function addTodo() {
      if (newTodo.value) {
        todos.value.push({
          done: false,
          content: newTodo.value
        });
        newTodo.value = '';
        saveData();
      }
    };

    function removeTodo(index) {
      todos.value.splice(index, 1);
      saveData();
    };

    function doneTodo(index) {
      todos.value[index].done = !todos.value[index].done;
      saveData();
    }

    function saveData() {
      const storageData = JSON.stringify(todos.value);
      localStorage.setItem('todos', storageData);
    }

    function saveNewInput(newText, index) {
      todos.value[index].content = newText;
      saveData();
    }

    return {
      newTodo,
      todos,
      addTodo,
      removeTodo,
      doneTodo,
      saveNewInput
    };
  },
};
</script>

<style>
body {
  background-color: #27292d;
}

#app {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  overflow: auto;
}

h1 {
  color: white;
  text-align: center;
}

form {
  display: flex;
	flex-direction: column;
  width: 100%;
  gap: 15px;
}

label, span {
  color: white;
}

label {
  font-size: 20px;
}

input {
  background-color: transparent;
  color: white;
  border: 2px solid rgba(255, 255, 255, 0.35);
  height: 35px;
  font-size: 20px;
  padding-left: 7px;
}

input:focus{
  outline: none;
}

h2 {
  color: white;
  margin-top: 30px;
  border-bottom: 2px solid rgba(255, 255, 255, 0.35);
  padding-bottom: 10px;
}

ul {
  list-style-type: none;
}

li {
  margin-bottom: 10px;
  display: flex;
  align-items: center;
  gap: 15px;
}

.input-checkbox {
  width: 20px;
}

.input-list {
  width: 400px;
  height: 25px;
  font-size: 15px;
}

.button-remove {
  height: 25px;
  width: 30px;
}

.button-add {
  height: 35px;
  font-size: 20px;
}

.done {
  text-decoration: line-through;
}

.no-item-text {
  width: 540px;
  color: white;
  text-align: center;
}
</style>