<template>
  <header class="header">
    <div class="header__container">
      <div class="header__wrapper">
        <div class="header__logo logo">
          <router-link to="/">
            <img
              class="header__logo-image"
              src="../assets/images/logo.svg"
              alt="logo"
            />
          </router-link>
        </div>
        <div class="header__login" @click="showModal">
          <span>Вход</span>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "TodoHeader",
  data() {
    return {
      showModal: false,
    };
  },
};
</script>

<style scoped lang="scss">
.header {
  padding: 23px 0;
  margin: 0 0 60px 0;

  &__container {
    max-width: 1840px;
    margin: 0 auto;
    padding: 0 20px;
  }

  &__wrapper {
    display: flex;
    justify-content: space-between;
  }

  &__logo {
    cursor: pointer;

    &-image {
      display: block;
    }
  }
}
</style>
