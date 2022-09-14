<template>
  <div class="item-task">
    <div class="item-task__state">
      <input
        type="checkbox"
        class="item-task__checkbox"
        @change="stateItem"
        :checked="stateCompleted"
      />
    </div>
    <div
      class="item-task__text"
      :contenteditable="edit"
      :class="{ done: stateCompleted, active: edit }"
      @input="getNewValue"
      @keyup.enter="setNewValue"
    >
      <span>{{ todoItem.text }}</span>
    </div>
    <div class="item-task__btn">
      <div class="item-task__edit" v-if="edit" @click="setNewValue">
        <img
          class="item-task__edit-img"
          src="../assets/images/check.svg"
          alt="edit"
        />
      </div>
      <div class="item-task__accept" v-else @click="editItem">
        <img
          class="item-task__edit-img"
          src="../assets/images/edit.svg"
          alt="edit"
        />
      </div>
    </div>
    <div class="item-task__btn">
      <div class="item-task__delete" v-if="edit" @click="cancelInput">
        <img
          class="item-task__delete-img"
          src="../assets/images/cross.svg"
          alt="delete"
        />
      </div>
      <div class="item-task__clear" v-else @click="removeItem">
        <img
          class="item-task__delete-img"
          src="../assets/images/delete.svg"
          alt="delete"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    todoItem: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      edit: false,
      text: "",
    };
  },
  methods: {
    removeItem() {
      this.$emit("remove-todo", this.todoItem.id);
    },
    stateItem() {
      this.$emit("stateItem", this.todoItem.id);
    },
    editItem() {
      this.edit = !this.edit;
    },
    setNewValue() {
      this.$emit("setNewValue", {
        id: this.todoItem.id,
        value: this.text || this.todoItem.text,
      });
      this.edit = !this.edit;
    },
    getNewValue(value) {
      console.log("метод change");
      this.text = value.target.textContent;
    },
    cancelInput() {
      this.text = this.todoItem.text;
    },
  },
  computed: {
    stateCompleted() {
      return this.todoItem.completed;
    },
  },
  mounted() {
    console.log("маунт++");
    this.text = this.todoItem.text;
  },
};
</script>

<style scoped lang="scss">
.item-task {
  display: flex;
  align-items: flex-start;
  padding: 20px 16px;
  width: 1000px;
  height: 64px;
  background: #ffffff;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.1);
  border-radius: 2px;
  margin: 0 0 10px 0;

  &:hover {
    background-color: #e6f7ff;
  }

  &:hover &__text {
    font-family: "Inter", sans-serif;
    font-style: normal;
    font-weight: 500;
    font-size: 16px;
    line-height: 22px;
    color: #464646;
  }

  &__state {
    margin: 0 24px 0 0;
  }

  &__text {
    flex: 1 1 750px;
    font-family: "Inter", sans-serif;
    font-style: normal;
    font-weight: 400;
    font-size: 16px;
    line-height: 24px;
    color: #464646;
    margin: 0 24px 0 0;
  }

  &__edit {
    cursor: pointer;
    user-select: none;
    margin: 0 16px 0 0;
  }

  &__delete {
    cursor: pointer;
    user-select: none;
  }
}

.done {
  text-decoration-line: line-through;
}

.active {
  font-family: "Inter", sans-serif;
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 24px;
  /* identical to box height, or 150% */

  display: flex;
  align-items: center;

  /* Secondary_text */

  color: #606060;
  border: 1px solid #dbe0e9;
}
</style>
