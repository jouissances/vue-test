<template>
  <div class="app-container">
    <h2 class="title">to-do list</h2>
    <div class="todo-list-wrapper">
      <span class="cleared" v-if="todos.length === 0">All clear! 🎉 You're a champion.</span>
      <ul class="todo-list">
        <li v-for="todo in todos" :key="todo.id" :class="{ 'completed':todo.completed }">
          <input type="checkbox" v-model="todo.completed" />
          <span>{{ todo.text }}</span>
          <button @click="removeTodo(todo)">
            <sub>Delete</sub>
          </button>
        </li>
      </ul>
    </div>

    <div class="input-wrapper">
      <label class="todo" for="text">add to-do:</label>
      <input type="text" id="text" v-model="newTodo" @keyup.enter="addTodo()" />
    </div>
  </div>
</template>

<script>
const listItems = [
  {
    id: 1,
    text: "walk alfie",
    completed: true
  },
  {
    id: 2,
    text: "save the world",
    completed: false
  }
];

export default {
  name: "todo",
  data() {
    return {
      todos: listItems,
      newTodo: ""
    };
  },
  methods: {
    addTodo() {
      let newID = listItems.length + 1;
      listItems.push({
        id: newID,
        text: this.newTodo,
        completed: false
      });
      this.newTodo = "";
    },

    removeTodo(todo) {
      this.todos.splice(this.todos.indexOf(todo), 1);
    }
  }
};
</script>

<style scoped>
.todo-list-wrapper {
  text-align: left;
  margin: 8vh 20vw;
  padding: 15px 0;
}

ul {
  position: relative;
}

li {
  list-style: none;
  margin-top: 5px;
}

label {
  font-weight: bold;
}

input {
  /* display: block; */
  margin-left: 15px;
  border: none;
  border-bottom: 1px solid slategrey;
}

.completed {
  /* color: red; */
  text-decoration: line-through;
}

ul li button {
  border: none;
  font-size: 0.65rem;
  text-align: right;
  text-decoration: none;
  position: absolute;
  right: 30px;
  cursor: pointer;
}

.cleared {
  display: block;
  text-align: center;
  position: relative;
  top: 5px;
}
</style>