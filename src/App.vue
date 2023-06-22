<template>
  <Navbar :logo="logo_src" :alt="app_name" />
  <router-view />
  <Footer />
</template>

<script>
import Navbar from "./components/Navbar.vue";
import Footer from "./components/Footer.vue";

export default {
  components: { Navbar, Footer },
  data() {
    return {
      logo_src: "/img/logo.png",
      app_name: "Make Your Burger",
    };
  },
  mounted() {
    document.title = "Make Your Burger";
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,100;0,300;0,400;0,700;0,900;1,100;1,300;1,400;1,700;1,900&display=swap");

* {
  font-family: "Lato", sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.main-container {
  margin: 50px;
  min-height: 400px;
}

h1 {
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #222;
}
</style>
