<template>
  <li :class="{ done: todo.completed }">
    <div>
        <input type="checkbox" id="checkbox" v-model="todo.completed">
        <strong>{{ index + 1 }}</strong>
        <span class="title">{{ todo.title }}</span>
    </div>
    <button class="delete" @click="$emit('delete-todo', todo.id)">
      &times;
    </button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
    index: Number,
  },
};
</script>

<style scoped>
li {
  border: 1px solid rgb(3, 85, 85);
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.4rem 2rem;
  margin-bottom: 0.6rem;
  overflow: hidden;
  position: relative;
  padding-left: 0.8rem;
}
.title {
  margin-left: 5px;
}
input {
  margin-right: 1rem;
}
.delete {
  cursor: pointer;
  font-size: 20px;
  background-color: rgb(247, 81, 81);
  color: white;
  border-radius: 15px;
  border: 1px solid transparent;
  margin-left: 10px;
}
.delete:hover {
  background-color: white;
  color: red;
  border: 1px solid red;
}
.delete:focus,
.delete:active {
  outline-width: 0;
}
.done {
  background: rgb(178, 250, 188);
}
.done .title {
  text-decoration: line-through;
}
</style>