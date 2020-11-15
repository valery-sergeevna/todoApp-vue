<template>
  <form @submit.prevent="addItem">
    <input type="text" placeholder="Enter a task..." v-model="title" />
    <div class="btn-container">
        <button type="submit">Create</button>
        <button @click.prevent="clearAll">Clear All</button>
    </div>
  </form>
</template>


<script>
export default {
  props: ["todos", "clearAll"],
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addItem() {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false
        };
        this.$emit("add-item", newTodo);
      }
      this.title = "";
    },
  },
};
</script>


<style scoped>
form {
  display: flex;
  justify-content: space-between;
}
input {
  width: 60%;
  padding: 10px;
  font-size: 16px;
}
input:focus {
  outline: 1px solid aqua;
}
.btn-container{
    width:40%;
    display: flex;
    justify-content: space-between;
    margin-left: 5px;
}
button {
  width: 48%;
  cursor: pointer;
  padding: 10px;
  font-size: 14px;
  background: aqua;
  border: 2px solid transparent;
}
button:hover {
  background: rgb(188, 255, 255);
  border: 2px solid aqua;
  margin-left: 2px;
}
@media screen and (max-width: 780px) {
  form {
    flex-direction: column;
  }
  input {
    width: 100%;
  }
  .btn-container{
      margin-top: 10px;
      width:100%;
      margin-left: 0;
  }
  button {
    width: 49%;
  }
}
</style>
