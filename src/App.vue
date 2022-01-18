<template>
  <div class="todo-app">
    <div class="wrapper">
      <div class="head">
        <img src="./assets/teflon-panna.svg" alt="teflon panna" />
        <h1>TEFLON</h1>
        <p>när det inte fastnar</p>
      </div>

      <TodoList :todos="todos" @delete="removeTodo" />

      <div class="inputField">
        <input
          class="inputBox"
          type="text"
          placeholder="Yoghurt med ketchupsmak"
          v-model="inputVal"
          @keydown.enter="pushInput(inputVal)"
        />
        <!--When enter is pressed, run pushInput(inputVal) -->
        <button @click="pushInput(inputVal)" class="inputButton">
          Add Todo
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";
export default {
  components: {
    TodoList,
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          content: "HTML",
          completed: true,
        },
        {
          id: 2,
          content: "CSS",
          completed: true,
        },
        {
          id: 3,
          content: "JavaScript",
          completed: false,
        },
        {
          id: 4,
          content: "Vue",
          completed: false,
        },
        {
          id: 5,
          content: "React",
          completed: false,
        },
      ],
      inputVal: "",
    };
  },
  methods: {
    pushInput(inputVal) {
      if (inputVal === "") {
        alert("Please enter your todo");
        return;
      }
      this.todos.push({
        id: this.todos.length + 1,
        content: inputVal,
        completed: false,
      });
      this.inputVal = "";
    },
    removeTodo(todo) {
      this.todos = this.todos.filter((item) => item.id !== todo.id);
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Titillium+Web:wght@300;600;700&display=swap");

body {
  background-color: #eee;
  font-family: "Titillium Web", sans-serif;
  display: grid;
  place-items: center;
}

.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100vh;
}

.head {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.head > p {
  font-size: 0.8rem;
  margin-top: 0;
}

.inputField {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 350px;
  background-color: gainsboro;
  margin-top: 5%;
  border: 1px solid #292929;
}

.inputBox {
  width: 98%;
  height: 60px;
  border: 0;
  text-align: center;
  font-size: 1rem;
}

.inputButton {
  width: 100%;
  height: 60px;
  color: white;
  background-color: #292929;
  border: 0;
  font-size: 1rem;
  font-weight: bold;
}
</style>
