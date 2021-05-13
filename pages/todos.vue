<template>
    <div class="container">
        <!-- <h1 class="title">TodoList</h1>
        <input placeholder="タスク追加" @keyup.enter="addTodo" class="textbox">
        <button class="button">追加</button>
        <ul>
            <li v-for="(todo, index) in todos" :key="index">
                <input type="checbox" @change="toggle">
                <span>{{ todo.text }}</span>
            </li>
        </ul> -->
        <h1 class="title">TodoList</h1>
        <ul>
            <li v-for="todo in todos" :key="todo.text">
                <input :checked="todo.done" @change="toggle(todo)" type="checkbox">
                <span :class="{ done: todo.done }">{{ todo.text }}</span>
            </li>
            <li><input @keyup.enter="addTodo" placeholder="What needs to be done?" class="textbox"></li>
        </ul>
    </div>
</template>

<script>
import { mapMutations } from 'vuex'

export default {
  computed: {
    todos () {
      return this.$store.state.todos.list
    }
  },
  methods: {
    addTodo (e) {
      this.$store.commit('todos/add', e.target.value)
      e.target.value = ''
    },
    ...mapMutations({
      toggle: 'todos/toggle'
    })
  }
}
</script>

<style scoped>
/* * {
    outline: 1px solid;
} */
.container{
    margin: 20px;
    max-width: 80%;
}
.title {
    font-size: 40px;
    color: #191970;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    margin-bottom: 10px;
}
ul {
    text-align: left;
    /* list-style: none; */
}
.textbox {
    display: inline-block;
    border-radius: 4px;
    border: 1px solid #191970;
    color: #191970;
    text-decoration: none;
    padding: 13px 30px;
}
li {
    color: #191970;
    text-decoration: none;
    padding: 13px 30px;
}
.button {
    display: inline-block;
    border-radius: 4px;
    border: 1px solid #191970;
    color: #191970;
    text-decoration: none;
    padding: 10px 30px;
}
.button:hover {
    color: #fff;
    background-color: #191970;
}
.done {
  text-decoration: line-through;
}
</style>