<template>
  <div id="app">
    <h1>App</h1>
    <AddTodo @add-todo="addTodo" />
    <hr />
    <TodoList v-bind:todos="todos" @remove-todo="removeTodo" />
    <StepSequencer
      v-bind:steps="steps"
      v-bind:stepAmount="stepAmount"
      @run-sequence="runSequence"
    />
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";
import AddTodo from "@/components/AddTodo";
import StepSequencer from "@/components/StepSequencer";
export default {
  name: "app",
  data() {
    return {
      stepAmount: 2,
      todos: [
        { id: 1, title: "buy something1", completed: false },
        { id: 2, title: "buy something2", completed: false },
        { id: 3, title: "buy something3", completed: false },
      ],
      steps: [
        { id: 1, midi: "note a", osc: "osc note a", active: false },
        { id: 2, midi: "note c", osc: "osc note c", active: false },
        // { id: 3, midi: "note a", osc: "osc note a", active: false },
        // { id: 4, midi: "note c", osc: "osc note c", active: false },
      ],
    };
  },
  components: {
    TodoList,
    AddTodo,
    StepSequencer,
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter((t) => t.id !== id);
    },
    addTodo(todo) {
      this.todos.push(todo);
    },
    runSequence() {
      this.steps.forEach((element) => {
        // console.log(element);
        // element.active = true;
        setInterval(()=>{element.active = !element.active},1000);
        element.active = !element.active;
      });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
