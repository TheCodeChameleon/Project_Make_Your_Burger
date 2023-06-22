<template>
  <div>
    <nav>
      <router-link to="/" id="logo-url">
        <img :src="logo" :alt="alt" id="logo" />
      </router-link>
      <router-link to="/">Home</router-link>
      <router-link to="/orders">Orders</router-link>
    </nav>
  </div>
</template>

<script>
export default {
  name: "Navbar",
  props: ["logo", "alt"],
};
</script>

<style scoped>
nav {
  background-color: #000000;
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  padding: 15px 50px;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}

#logo-url {
  margin: auto;
  margin-left: 0;
}

#logo {
  width: 40px;
  height: 40px;
}

nav a {
  color: #fbcb31;
  text-decoration: none;
  margin: 12px;
  transition: 0.5s;
}

nav a:hover {
  color: white;
}
</style>
