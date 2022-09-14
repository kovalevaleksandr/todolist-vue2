<template>
  <div class="task-creator">
    <div class="task-creator__container">
      <div class="task-creator__wrapper">
        <input
          type="text"
          class="task-creator__input"
          placeholder="Введите название задания"
          v-model="text"
          @keyup.enter="addTask"
        />
        <AddTaskBtn @addTask="addTask" />
      </div>
    </div>
  </div>
</template>
<script>
import AddTaskBtn from "@/components/BtnAdd";
export default {
  name: "TodoInput",
  components: {
    AddTaskBtn,
  },
  data() {
    return {
      text: "",
    };
  },
  methods: {
    addTask() {
      if (this.text.trim()) {
        const newTodo = {
          id: Date.now(),
          text: this.text,
          completed: false,
        };

        this.$emit("add-todo", newTodo);
        this.text = "";
      }
    },
  },
};
</script>
<style scoped lang="scss">
.task-creator {
  background: #ffffff;
  margin: 0 0 40px 0;

  &__container {
    max-width: 1040px;
    margin: 0 auto;
    padding: 0 20px;
  }

  &__wrapper {
    display: flex;
    width: 100%;
  }

  &__input {
    flex: 1;
    width: 100%;
    padding: 8px 12px;
    border: 1px solid #dbe0e9;
    box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.1);
    border-radius: 2px 0 0 2px;

    &:focus {
      border: 1px solid #1859ff;
    }

    &:focus::placeholder {
      color: transparent;
    }

    &::-webkit-input-placeholder {
      font-family: "Inter", sans-serif;
      font-style: normal;
      font-weight: 400;
      font-size: 16px;
      line-height: 24px;
      color: #b4bac4;
    }
  }
}
</style>
