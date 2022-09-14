<template>
  <div>
    <div class="modal">
      <div class="modal__container">
        <div class="modal__wrapper">
          <div class="modal__title">
            <h1>Exceed To-Do list</h1>
          </div>
          <div class="modal__desc">
            <span>Пожалуйста, выполните вход или регистрацию в системе</span>
          </div>
          <div class="modal__btn">
            <div class="modal__btn-auth">
              <span>Вход</span>
            </div>
            <div class="modal__btn-reg">
              <span>Регистрация</span>
            </div>
          </div>
          <TodoLogin />
          <TodoReg />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TodoLogin from "./Auth/TodoLogin";
export default {
  name: "ModalAuth",
  components: {
    TodoLogin,
  },
};
</script>

<style scoped></style>
