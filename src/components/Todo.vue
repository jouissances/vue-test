<template>
  <div class="app-container">
    <h2 class="title">To-do List</h2>
    <div class="todo-list-wrapper">
      <ul class="todo-list">
        <li v-for="todo in todos" :key="todo.id" :class="{ 'completed':todo.completed }">
          <input type="checkbox" v-model="todo.completed" />
          <span>{{ todo.text }}</span>
        </li>
      </ul>
    </div>

    <div class="input-wrapper">
      <label class="todo" for="text">add todo:</label>
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
    }
  }
};
</script>

<style scoped>
.todo-list-wrapper {
  text-align: left;
  margin: 8vh 25vw;
  padding: 15px 0;
}

li {
  list-style: none;
  margin-top: 5px;
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
</style>