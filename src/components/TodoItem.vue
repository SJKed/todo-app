<template>
  <div class="todoItem">
    <input type="checkbox" class="check" />
    <p>{{ todos.content }}</p>
    <img
      src="../assets/delete.svg"
      alt=""
      class="delete"
      @click="$emit('delete')"
    />
  </div>
</template>

<script>
export default {
  props: ["todos"],
};
</script>

<style>
.todoItem {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 350px;
  background-color: gainsboro;
  margin: 2px;
}

.check {
  width: 20px;
  height: 20px;
  border: 1px solid #ccc;
  border-radius: 10px;
  cursor: pointer;
  margin-left: 5%;
}

.delete {
  width: 20px;
  height: 20px;
  border: 1px solid #ccc;
  border-radius: 10px;
  cursor: pointer;
  margin-right: 5%;
}
</style>
