<template>
  <Banner />
  <div class="main-container">
    <h1>Make Your Burger</h1>
    <Form />
  </div>
</template>

<script>
import Banner from "@/components/Banner.vue";
import Form from "@/components/Form.vue";

export default {
  name: "HomeView",
  components: {
    Banner,
    Form,
  },
};
</script>
