<template>
  <div class="filter">
    <div class="filter__container">
      <div class="filter__wrapper">
        <div class="filter__btn" @click="allTodo">
          <span>Все задания</span>
        </div>
        <div class="filter__btn" @click="activeTodo">
          <span>Активные задания</span>
        </div>
        <div class="filter__btn" @click="completedTodo">
          <span>Выполненные задания</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoFilter",
  props: ["todoList"],
  data() {
    return {};
  },
  methods: {
    allTodo() {
      this.$emit("allTodo");
    },
    activeTodo() {
      this.$emit("activeTodo");
    },
    completedTodo() {
      this.$emit("completedTodo");
    },
  },
};
</script>

<style scoped lang="scss">
.filter {
  margin: 0 0 20px 0;

  &__container {
    max-width: 1040px;
    margin: 0 auto;
    padding: 0 20px;
  }

  &__wrapper {
    display: flex;
  }

  &__btn {
    display: flex;
    align-items: flex-start;
    padding: 2px 8px;
    margin: 0 20px 0 0;
    background: #ffffff;
    border: 1px solid #dbe0e9;
    box-shadow: 0 2px 0 rgba(0, 0, 0, 0.016);
    border-radius: 2px;
    font-family: "Inter", sans-serif;
    font-style: normal;
    font-weight: 400;
    font-size: 16px;
    line-height: 24px;
    text-align: center;
    color: #606060;
    cursor: pointer;
    user-select: none;

    &--active {
      font-family: "Inter", sans-serif;
      font-style: normal;
      font-weight: 400;
      font-size: 16px;
      line-height: 24px;
      text-align: center;
      color: #1859ff;
      border: 1px solid #1859ff;
      box-shadow: 0 2px 0 rgba(0, 0, 0, 0.016);
    }
  }
}
</style>
