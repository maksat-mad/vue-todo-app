<template>
  <div>
    <h1>ToDo App</h1>
    <form>
      <label>New ToDo List</label>
      <input 
        type="text" 
        name="newTodo" 
        placeholder="I will do..."
        autocomplete="off" 
      />
      <button class="button-add">Add ToDo</button>
    </form>
    <h2>ToDo List</h2>
    <ul>
      <li>
        <input 
          type="checkbox" 
          class="input-checkbox"
        />
        <input 
          type="text" 
          class="input-list" 
          value="Lorem ipsum, dolor sit amet" 
          autocomplete="off"
        />
        <button 
          class="button-remove"
        >&#10006;</button>
      </li>
      <li>
        <input 
          type="checkbox" 
          class="input-checkbox"
        />
        <input 
          type="text" 
          class="input-list" 
          value="Lorem ipsum, dolor sit amet" 
          autocomplete="off"
        />
        <button 
          class="button-remove"
        >&#10006;</button>
      </li>
      <li>
        <input 
          type="checkbox" 
          class="input-checkbox"
        />
        <input 
          type="text" 
          class="input-list" 
          value="Lorem ipsum, dolor sit amet" 
          autocomplete="off"
        />
        <button 
          class="button-remove"
        >&#10006;</button>
      </li>
    </ul>
  </div>
</template>

<script>
// import { ref } from 'vue';

export default {
  name: "App",
  setup() {
    // const newTodo = ref('');
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
</style>
