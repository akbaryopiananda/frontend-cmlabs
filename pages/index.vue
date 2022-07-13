<template>
  <div>
    <Header/>
        <div class="text-center" style="margin-top:100px; margin-bottom:100px">
            <b-icon icon="emoji-smile" variant="danger" style="width: 70px; height: 70px;" ></b-icon>
            <b-icon icon="emoji-laughing" variant="danger" style="width: 70px; height: 70px;" ></b-icon>
            <b-icon icon="emoji-heart-eyes" variant="danger" style="width: 70px; height: 70px;" ></b-icon>
            <p>meal API Website</p>
            <p class="h1">See All The Delicious Foods</p>
        </div>
        <div class="section-content">
        <b-container>
            <b-row class="mb-3 text-center">
            <b-col v-for="(product, i) in category.slice(0, 4)" :key="i">
                <b-button
                :to="{
                    name: 'Category-list_name',
                    params: { name: product.strCategory },
                }"
                style="max-width: 20rem"
                variant="light"
                >
                <b-img :src="product.strCategoryThumb" style="width: 13rem" rounded alt="Rounded image"></b-img>

                <!-- <img :src="product.strCategoryThumb" style="width: 13rem" /> -->
                <h2 class="text-center text-dark">
                    {{ product.strCategory }}
                </h2>
                </b-button>
            </b-col>
            </b-row>
            <b-row class="mb-3 text-center">
            <b-col v-for="(product, i) in category.slice(5, 9)" :key="i">
                <b-button
                :to="{
                    name: 'Category-list_name',
                    params: { name: product.strCategory },
                }"
                style="max-width: 20rem"
                variant="light"
                >
                <b-img :src="product.strCategoryThumb" style="width: 13rem" rounded alt="Rounded image"></b-img>
                <h2 class="text-center text-dark">
                    {{ product.strCategory }}
                </h2>
                </b-button>
            </b-col>
            </b-row>
            <b-row class="mb-3 text-center">
            <b-col v-for="(product, i) in category.slice(10, 14)" :key="i">
                <b-button
                :to="{
                    name: 'Category-list_name',
                    params: { name: product.strCategory },
                }"
                style="max-width: 20rem"
                variant="light"
                >
                <b-img :src="product.strCategoryThumb" style="width: 13rem" rounded alt="Rounded image"></b-img>
                <h2 class="text-center text-dark">
                    {{ product.strCategory }}
                </h2>
                </b-button>
            </b-col>
            </b-row>
            <b-row class="mb-3 text-center">
            <b-col v-for="(product, i) in category.slice(15, 19)" :key="i">
                <b-button
                :to="{
                    name: 'Category-list_name',
                    params: { name: product.strCategory },
                }"
                style="max-width: 20rem"
                variant="light"
                >
                <b-img :src="product.strCategoryThumb" style="width: 13rem" rounded alt="Rounded image"></b-img>
                <h2 class="text-center text-dark">
                    {{ product.strCategory }}
                </h2>
                </b-button>
            </b-col>
            </b-row>
        </b-container>
        </div>
  </div>
</template>

<script>
import { mapActions, mapState } from "vuex";
export default {
  async asyncData({ store }) {
    await Promise.all([store.dispatch("category/getCategoryData")]);
    return;
  },
  data() {
    return {
      fields: ["idCategory"],
      product: [],
    };
  },
  computed: {
    ...mapState("category", {
      category: (state) => state.category,
    }),
  },
  methods: {
    ...mapActions("category", ["getCategoryData"]),
  },
}
</script>
