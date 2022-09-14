<template>
  <div>
    <footer class="footer">
      <div class="footer__container">
        <div class="footer__logo">
          <router-link to="/">
            <img
              class="footer__logo-img"
              src="../assets/images/logo-footer.svg"
              alt="logo"
            />
          </router-link>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: "TodoFooter",
};
</script>

<style scoped lang="scss">
@import "../assets/styles/_colors.scss";
.footer {
  background-color: $Background_footer;
  box-shadow: inset 0px -1px 0px $Background_footer;
  padding: 23px 0;

  &__container {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  &__logo {
  }
}
</style>
