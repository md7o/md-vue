<template>
  <div class="ListHeader">
    <div class="logo">MD Store</div>
    <ul id="nav">
      <router-link :to="'/'"
        ><li><a>Shirt</a></li></router-link
      >
      <router-link :to="'/BootsPage'"
        ><li><a>Boots</a></li></router-link
      >
    </ul>
  </div>
</template>

<script>
export default {
  name: "ListHeader",
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.ListHeader {
  width: 100%;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  background-image: linear-gradient(
    to right,
    rgb(53, 117, 98),
    rgb(119, 214, 155)
  );
}

.logo {
  color: white;
  font-size: 30px;
}
ul {
  display: flex;
  justify-content: center;
  align-items: center;
  list-style: none;
}
ul a {
  color: white;
  text-decoration: none;
  font-size: 25px;
  padding: 20px 15px;
  transition: all ease 0.2s;
}

ul a:hover {
  background-color: rgb(119, 214, 155);
}
</style>
