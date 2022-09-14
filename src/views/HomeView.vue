<template>
  <div class="home">
    <InputTask @add-todo="addTask" />
    <FilterBtn
      @activeTodo="activeTodo"
      @allTodo="allTodo"
      @completedTodo="completedTodo"
    />
    <TodoList
      @remove-todo="removeTask"
      :todoList="todoList"
      @setNewValue="setNewValue"
      @stateItem="stateItem"
    />
  </div>
</template>
<script>
import InputTask from "@/components/Input";
import FilterBtn from "@/components/Filter";
import TodoList from "@/components/List";
export default {
  name: "HomeView",
  components: {
    InputTask,
    FilterBtn,
    TodoList,
  },
  data() {
    return {
      todoList: [],
    };
  },
  mounted() {
    this.todoList = JSON.parse(localStorage.todolist) || [];
  },
  methods: {
    addTask(todo) {
      this.todoList.push(todo);
      localStorage.setItem("todolist", JSON.stringify(this.todoList));
    },
    setNewValue(obj) {
      const editObj = this.todoList.find((i) => i.id === obj.id);
      editObj.text = obj.value;
      localStorage.setItem("todolist", JSON.stringify(this.todoList));
    },
    removeTask(id) {
      this.todoList = this.todoList.filter((i) => i.id !== id);
      localStorage.setItem("todolist", JSON.stringify(this.todoList));
    },
    stateItem(id) {
      const index = this.todoList.findIndex((i) => i.id === id);
      this.todoList[index].completed = !this.todoList[index].completed;
      localStorage.setItem("todolist", JSON.stringify(this.todoList));
    },
    allTodo() {
      this.todoList = JSON.parse(localStorage.todolist) || [];
    },
    activeTodo() {
      this.todoList = JSON.parse(localStorage.todolist) || [];
      this.todoList = this.todoList.filter((i) => !i.completed);
    },
    completedTodo() {
      this.todoList = JSON.parse(localStorage.todolist) || [];
      this.todoList = this.todoList.filter((i) => i.completed);
    },
  },
};
</script>
<style scoped lang="scss">
.home {
  min-height: 100%;
  display: flex;
  flex-direction: column;
}

.main {
  flex: 1 1 auto;
}
</style>
