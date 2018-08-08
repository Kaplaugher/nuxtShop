<template>
  <v-container grid-list-lg>
    <v-layout row wrap>
      <v-flex xs12 sm6 class="product-image">
        <img :src="image" alt="" class="img">
      </v-flex>
      <v-flex xs12 sm6 class="product-info">
        <h1 class="display-2">{{product}}</h1>
        <p v-if="inventory > 10" class="subheading">In Stock</p>
        <p v-else-if="inventory > 0 && inventory > 0">Almost Sold Out!</p>
        <p v-else class="subheading">Out of Stock</p>

        <ul>
          <li v-for="detail in details">{{detail}}</li>
        </ul>

        <v-select
            :items="sizes"
            label="Choose A Size"
            outline
        ></v-select>
          <div v-for="variant in variants" :key="variant.variantId">
            {{ variant.variantColor }}
          </div>

        </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      product: "tshirt 1",
      image:
        "https://res.cloudinary.com/kaptivating-io/image/upload/f_auto/v1533688012/onlineStore/vmSocks-green-onWhite.jpg",
      inStock: true,
      inventory: 100,
      details: ["80% cotton", "20% polyester", "Gender-neutral"],
      variants: [
        {
          variantId: 2234,
          variantColor: "green"
        },
        {
          variantId: 2235,
          variantColor: "blue"
        }
      ],
      sizes: ["Large", "Medium", "Small", "X-Sm"]
    };
  }
};
</script>

<style>
.img {
  height: 450px;
}
</style>
