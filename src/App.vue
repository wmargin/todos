<template>
  <div class="title">TODOLIST</div>
  <TodoInput @add="newtask"></TodoInput>
  <TodoList :list="tasklist" class="mt-4"></TodoList>
  <TodoButton class="mt-4" v-model:active="activeIndex"></TodoButton>
</template>

<script>
import TodoList from "./components/todo-list/TodoList.vue"
import TodoInput from "./components/todo-input/TodoInput.vue"
import TodoButton from "./components/todo-button/TodoButton.vue"
export default {
  name: "MyApp",
  data() {
    return {
      todolist: [
        { id: 1, task: "周一招商干山", done: false },
        { id: 2, task: "feafnaiefnfaeif", done: false },
        { id: 3, task: "fgeigenfasnfn", done: true },
      ],
      nextid: 4,
      activeIndex: 0,
    }
  },
  components: {
    TodoList,
    TodoInput,
    TodoButton,
  },
  methods: {
    newtask(newt) {
      // console.log(newt)
      this.todolist.push({
        id: this.nextid,
        task: newt,
        done: false,
      })

      this.nextid++
    },
  },
  computed: {
    tasklist() {
      switch (this.activeIndex) {
        case 0:
          return this.todolist
        case 1:
          return this.todolist.filter((x) => x.done)
        case 2:
          return this.todolist.filter((x) => !x.done)
      }
    },
  },
}
</script>

<style lang="scss" scoped>
.title {
  font-size: 28px;
  font-weight: 700;
  text-decoration: underline;
  width: 400px;
  text-align: center;
  padding: 10px;
}
</style>
