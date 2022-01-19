<template>
  <div class="todo-app">
    <transition name="pop" appear>
      <TodoMenu v-if="showMenu" @close="showMenu = false" />
    </transition>
    <img
      src="./assets/menu.svg"
      alt="Menu icon"
      class="homeMenuBtn"
      @click="showMenu = true"
    />

    <div class="head">
      <img src="./assets/teflon-panna.svg" alt="teflon panna" />
      <h1>TEFLON</h1>
      <p>när det inte fastnar</p>
    </div>

    <TodoList :todos="todos" @delete="removeTodo" @checked="checkCompleted" />

    <div class="inputField">
      <input
        class="inputBox"
        type="text"
        placeholder="Yoghurt med ketchupsmak"
        v-model="inputVal"
        @keydown.enter="pushInput(inputVal)"
      />
      <button @click="pushInput(inputVal)" class="inputButton">Add Todo</button>
    </div>
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";
import TodoMenu from "./components/TodoMenu.vue";
export default {
  components: {
    TodoList,
    TodoMenu,
  },
  data() {
    return {
      todos: [
        { id: 1, content: "HTML", completed: true },
        { id: 2, content: "CSS", completed: true },
        { id: 3, content: "JavaScript", completed: false },
        { id: 4, content: "Vue", completed: false },
        { id: 5, content: "React", completed: false },
      ],
      inputVal: "",
      showDone: true,
      showMenu: false,
    };
  },
  computed: {
    completedTodos() {
      return this.todos.filter((item) => item.completed);
    },
    incompletedTodos() {
      return this.todos.filter((item) => !item.completed);
    },
  },
  methods: {
    pushInput(inputVal) {
      if (inputVal === "") {
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
    checkCompleted(todo) {
      console.log("pog");
      if (todo.completed) {
        todo.completed = false;
      } else {
        todo.completed = true;
      }
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Titillium+Web:wght@300;600;700&display=swap");

body {
  background-color: #292929;
  font-family: "Titillium Web", sans-serif;
  display: grid;
  place-items: center;
}

.todo-app {
  width: 350px;
  height: 600px;
  background-color: #fff;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
  padding: 20px;
  margin-top: 5%;
}

.head {
  position: sticky;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-top: 10%;
}
.head > p {
  font-size: 0.8rem;
  margin-top: -25px;
}
.head > h1 {
  font-size: 2rem;
  margin-top: 0;
}
.homeMenuBtn {
  margin-left: auto;
  width: 30px;
  height: 30px;
  cursor: pointer;
}

.inputField {
  position: sticky;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 350px;
  background-color: gainsboro;
  border: 1px solid #292929;
  margin-top: 5%;
}

.inputBox {
  width: 98%;
  height: 60px;
  border: 0;
  text-align: center;
  font-size: 1rem;
  outline: none;
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
.inputButton:active {
  width: 100%;
  height: 60px;
  color: white;
  background-color: #919191;
  border: 0;
  font-size: 1rem;
  font-weight: bold;
}

.pop-enter-active,
.pop-leave-active {
  transition: transform 0.4s cubic-bezier(0.5, 0, 0.5, 1), linear;
}

.pop-enter,
.pop-leave-to {
  opacity: 0;
  transform: translateX(50%);
}
</style>
