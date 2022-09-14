<template>
  <div class="task-creator__btn" @click.enter="addTask">
    <img class="task-creator__btn-img" src="@/assets/images/plus.svg" alt="+" />
    <span>Добавить задание</span>
  </div>
</template>

<script>
export default {
  name: "TodoBtnAdd",
  data() {
    return {};
  },
  methods: {
    addTask() {
      this.$emit("addTask");
    },
  },
};
</script>

<style scoped lang="scss">
.task-creator {
  &__btn {
    display: flex;
    justify-content: center;
    align-items: center;
    background: #1859ff;
    border: 1px solid #1859ff;
    font-family: "Inter", sans-serif;
    font-style: normal;
    font-weight: 400;
    font-size: 16px;
    line-height: 24px;
    color: #ffffff;
    padding: 8px 16px;
    cursor: pointer;
    user-select: none;

    &-img {
      margin: 0 8px 0 0;
    }
  }
}
</style>
