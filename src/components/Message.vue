<template>
  <div class="message-container">
    {{ msg }}
  </div>
</template>

<script>
export default {
  name: "Message",
  props: {
    msg: String,
  },
};
</script>

<style>
.message-container {
  color: #008000;
  background-color: #26f058;
  border: 2px solid #b8daff;
  border-radius: 5px;
  padding: 10px;
  max-width: 400px;
  margin: 30px auto;
  text-align: center;
  font-weight: bold;
}
</style>
