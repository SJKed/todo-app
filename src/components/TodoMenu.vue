<template>
  <div class="blackout">
    <div class="todoMenu">
      <img
        src="../assets/close.svg"
        alt="close menu button"
        class="closeBtn"
        @click="$emit('close')"
      />
      <button class="menuBtn">Hide done todos</button>
      <button class="menuBtn">Delete done todos</button>
      <button class="menuBtn pink">Clear all data</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["todos", "showMenu"],
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Titillium+Web:wght@300;600;700&display=swap");
.todoMenu {
  position: absolute;
  display: grid;
  grid-template-rows: repeat(8, 1fr);
  top: 8.6%;
  right: 36.5%;
  width: 20%;
  height: 640px;
  box-shadow: 0 5px 5px rgba(0, 0, 0, 0.2);
  background: rgb(236, 236, 236);
  z-index: 999;
  transform: none;
}

.menuBtn {
  width: 100%;
  height: 60px;
  color: white;
  background-color: gainsboro;
  color: black;
  text-align: left;
  border: 0;
  font-size: 1rem;
  font-family: "Titillium Web", sans-serif;
  cursor: pointer;
}

.menuBtn:hover {
  background-color: #292929;
}

.pink {
  background-color: rgba(255, 0, 0, 0.363);
  grid-row: 7;
}

.closeBtn {
  justify-self: end;
  margin-top: 20px;
  margin-right: 20px;
  width: 30px;
  height: 30px;
  cursor: pointer;
}
</style>
