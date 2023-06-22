<template>
  <div class="main-banner">
    <h1>Make Your Burger</h1>
  </div>
</template>

<script>
export default {
  name: "Banner",
};
</script>

<style scoped>
.main-banner {
  background-image: url("../../public/img/burger.jpg");
  background-position: 0 -250px;
  background-size: cover;
  background-repeat: no-repeat;
  height: 600px;
  display: flex;
  align-items: center;
  justify-content: flex-start;
}

.main-banner h1 {
  color: #fafffd;
  text-align: center;
  font-size: 60px;
  background-color: #000000;
  padding: 20px 40px;
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}

@media only screen and (max-width: 900px) {
  .main-banner {
    background-position: 0;
  }
}
</style>
