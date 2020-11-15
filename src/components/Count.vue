<template>
  <div class="count">
    <div class="count__item">
      <span>All:</span>
      <span class="number all">{{todos.length}}</span>
    </div>
    <div class="count__item">
      <span>Done:</span>
      <span class="number done">{{todos.filter(todo => todo.completed).length}}</span>
    </div>
  </div>
</template>

<script>
    export default {
        props: ['todos'],
    }
</script>

<style scoped>
.count{
    display: flex;
}
.count__item{
    margin-left: 10px;
}
span:nth-child(2n){
    margin-left: 10px;
}
.number{
    display: inline-block;
    padding:5px 10px;
    border-radius:50%;
    color:white;
    text-align: center;
}
.done{
    background: lightgreen;
    color:black;
}
.all{
    background: red;
}
</style>