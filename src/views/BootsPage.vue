/* eslint-disable vue/no-dupe-keys */
<template>
  <div class="boots">
    <div class="main">
      <img v-bind:src="image" class="boots_img" />

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
            <button>40</button>
            <button>41</button>
            <button>42</button>
            <button>43</button>
            <button>44</button>
            <button>45</button>
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
  name: "BootsPage",
  data() {
    return {
      cart: 0,
      selectedVariant: 0,
      desc: "Sport Boots",
      inStock: true,
      details: ["30% leather", "50% Rubber", "20% fabric"],
      size: "size available",
      variants: [
        {
          id: 2234,
          color: "black",
          image: require("../assets/blackB.png"),
          quantity: 50,
        },
        {
          id: 2235,
          color: "#8B4513",
          image: require("../assets/brownB.png"),
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

.boots_img {
  width: 52vh;
  height: 45vh;
  margin: 20px;
  border: 20px #d1d1d1b4 solid;
  padding: 20px;
  box-shadow: 1px 1px 10px 1px rgba(187, 187, 187, 0.712);
}
</style>
