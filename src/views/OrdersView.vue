<template>
  <div>
    <div class="main-container">
      <h1>Manage Orders:</h1>
      <div class="main-container-dashboard">
        <Dashboard />
      </div>
    </div>
    <div class="warning-text">
      <p>
        * This page is not available in a regular application; it is solely for
        demonstration purposes. In a real application, authentication would be
        required. *
      </p>
    </div>
  </div>
</template>

<script>
import Dashboard from "../components/Dashboard";

export default {
  name: "OrdersView",
  components: {
    Dashboard,
  },
};
</script>

<style scoped>
.warning-text {
  color: red;
  text-align: center;
  margin: 10px auto;
  font-style: italic;
}

.main-container-dashboard {
  overflow: scroll;
}
</style>
