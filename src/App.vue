<script>

import AddToDo from './components/AddToDo.vue'
import Tab from "./components/Tab.vue";
import Todo from "./components/Todo.vue";

export default {
  components: {
    Todo,
    Tab,
    AddToDo
  },
  data() {
    return {
      todos: [],
      'done': false
    }
  },
  computed: {
    undoneTodos() {
      return this.todos.filter(function (todo) {
        return !todo.done
      })
    },
    doneTodos() {
      return this.todos.filter(function (todo) {
        return todo.done
      })
    },
    isDone() {
      return !this.done;
    }
  },
  methods: {
    addToDo($text) {
      this.todos.push({
        key: this.todos.length + 1, done: false, text: $text
      })
    },
    deleteTodo($key) {
      this.todos = this.todos.filter(function ($todo) {
        return $todo.key !== $key
      })
    },
    doneTodo($key) {
      let index = this.todos.findIndex((obj => obj.key === $key));
      this.todos[index].done=true
    },
    undoneTodo($key) {
      let index = this.todos.findIndex((obj => obj.key === $key));
      this.todos[index].done=false
    }
  }
}
</script>

<template>
  <div class="container">
    <AddToDo @addToDo="addToDo"></AddToDo>
    <hr>
    <div class="row">
      <div class="col-5 mx-auto my-3">
        <ul class="nav nav-pills mb-3" id="pills-tab" role="tablist">
          <Tab :count="undoneTodos.length" t="undone" :active="isDone" @click="this.done=false"></Tab>
          <Tab :count="doneTodos.length" t="done" :active="!isDone" @click="this.done=true"></Tab>
        </ul>
        <div class="tab-content" id="pills-tabContent">
          <div class="tab-pane fade " :class="{show:isDone,active:isDone}">
            <Todo v-for="todo in undoneTodos" :t="todo.text" @deleteTodo="deleteTodo" :done="false"
                  :k="todo.key" @doneTodo="doneTodo"></Todo>
          </div>
          <div class="tab-pane fade" :class="{show:!isDone,active:!isDone}">
            <Todo v-for="todo in doneTodos" :t="todo.text" @deleteTodo="deleteTodo" :done="true"
                  :k="todo.key" @undoneTodo="undoneTodo"></Todo>
          </div>
          <div class="tab-pane fade " id="pills-profile" role="tabpanel" aria-labelledby="pills-profile-tab">...
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

