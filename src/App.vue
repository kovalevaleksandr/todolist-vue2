<template>
  <div id="app" class="app">
    <Header />

    <main class="main">
      <router-view />
    </main>

    <Footer />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
export default {
  name: "App",
  components: {
    Header,
    Footer,
  },
};
</script>

<style lang="scss">
.app {
  min-height: 100%;
  display: flex;
  flex-direction: column;
}

.main {
  flex: 1 1 auto;
}

/*nulling*/
*,
*::before,
*::after {
  outline: none;
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  border: 0;
}

a {
  text-decoration: none;
}

ul,
ol,
li {
  list-style: none;
}

html {
  height: 100%;
  box-sizing: border-box;
}

body {
  height: 100%;
  font-family: "Inter", sans-serif;
  min-width: 320px;
  margin: 0;
  padding: 0;
  font-size: 16px;
  line-height: 30px;
  font-weight: 400;
}

li {
  list-style: none;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  font-weight: inherit;
  font-size: inherit;
}

.image {
  display: block;
}
</style>
