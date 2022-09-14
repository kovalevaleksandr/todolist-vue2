<template>
  <div class="list">
    <div class="list__container">
      <ItemTask
        v-for="(todoItem, index) of todoList"
        :key="index"
        :todoItem="todoItem"
        @remove-todo="removeTodo"
        @setNewValue="setNewValue"
        @stateItem="stateItem"
      />
    </div>
  </div>
</template>

<script>
import ItemTask from "./Item";

export default {
  name: "TodoList",
  props: ["todoList"],
  components: {
    ItemTask,
  },
  data() {
    return {};
  },
  methods: {
    removeTodo(id) {
      this.$emit("remove-todo", id);
    },
    setNewValue(obj) {
      this.$emit("setNewValue", obj);
    },
    stateItem(id) {
      this.$emit("stateItem", id);
    },
  },
};
</script>

<style scoped lang="scss">
.list {
  display: flex;
  flex-direction: column;
  width: 100%;

  &__container {
    max-width: 1040px;
    margin: 0 auto;
    padding: 0 20px;
  }
}
</style>
