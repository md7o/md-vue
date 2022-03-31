/* eslint-disable vue/no-dupe-keys */
<template>
  <div class="HomeStore">
    <div class="main">
      <img v-bind:src="image" class="shirt_img" />

      <div class="shir_type">
        <div class="description">
          <h1>{{ title }}</h1>
          <p v-if="inStock">in Stock</p>
          <p v-else>out of Stock</p>
          <ul>
            <li v-for="detail in details" :key="detail">{{ detail }}</li>
          </ul>
          <div
            v-for="(variant, index) in variants"
            :key="variant.id"
            @mouseover="updateVariant(index)"
            class="color-circle"
            :style="{ backgroundColor: variant.color }"
          >
            {{}}
          </div>
          <div class="size">
            <p>{{ size }}</p>
            <button>M</button>
            <button>L</button>
          </div>

          <div>
            <button
              class="button"
              :class="{ disabledButton: !inStock }"
              :disabled="!inStock"
              @click="addToCart"
            >
              Add to cart
            </button>
          </div>
        </div>
      </div>
      <div class="Cart">cart({{ cart }})</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HomeStore",
  data() {
    return {
      cart: 0,
      selectedVariant: 0,
      desc: "Cotton Shirt",
      inStock: true,
      details: ["70% cotton", "10% wool", "20% polyester"],
      size: "size available",
      variants: [
        {
          id: 2234,
          color: "lightblue",
          image: require("../assets/blue.png"),
          quantity: 50,
        },
        {
          id: 2235,
          color: "Black",
          image: require("../assets/black.png"),
          quantity: 0,
        },
      ],
    };
  },
  methods: {
    addToCart() {
      this.cart += 1;
    },
    updateVariant(index) {
      this.selectedVariant = index;
    },
  },
  computed: {
    title() {
      return this.desc;
    },
    image() {
      return this.variants[this.selectedVariant].image;
    },
    // eslint-disable-next-line vue/no-dupe-keys
    inStock() {
      return this.variants[this.selectedVariant].quantity;
    },
  },
};
</script>
<style>
@import url("https://fonts.googleapis.com/css2?family=Josefin+Sans:ital,wght@1,200&family=Ubuntu&display=swap");

body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Ubuntu", sans-serif;
  background-color: rgb(233, 233, 233);
}

.main {
  display: flex;
  justify-content: space-evenly;
  align-content: center;
}
.Cart {
  background-color: rgb(255, 255, 255);
  border-radius: 10px;
  font-size: 20px;
  width: 10vh;
  height: 5vh;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 20px 0 0 100px;
}
.shirt_img {
  width: 45vh;
  height: 45vh;
  margin: 20px;
  border: 20px #d1d1d1b4 solid;
  padding: 20px;
  box-shadow: 1px 1px 10px 1px rgba(187, 187, 187, 0.712);
}

.description {
  margin-left: 150px;
  font-size: 30px;
}

.color-circle {
  width: 50px;
  height: 50px;
  border: 1px solid rgb(196, 196, 196);
  margin: 10px;
  border-radius: 10px;
  border: 3px solid rgba(104, 104, 104, 0.294);
  box-shadow: 1px 1px 5px 1px rgba(187, 187, 187, 0.712);
}

.disabledButton {
  background-color: rgb(233, 233, 233);
  cursor: not-allowed;
}

.size button {
  width: 30%;
  height: 60px;
  margin: 0 0 10px 10px;
  cursor: pointer;
  transition: ease 5s all;
}

.size button:hover {
  background-color: grey;
}

.button {
  border: none;
  background-color: rgb(212, 212, 212);
  margin: 10px 0 20px 10px;
  padding: 20px;
  cursor: pointer;
  transition: ease 0.3s all;
}

.button:hover {
  background-color: grey;
}

.size button {
  width: 30%;
  height: 60px;
  margin: 0 0 10px 10px;
  cursor: pointer;
  background-color: rgb(212, 212, 212);
  border: none;
  transition: ease 0.3s all;
}

.size button:hover {
  border: none;
  color: black;
}
</style>
