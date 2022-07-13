<template>
  <div>
    <Header />
    <b-container class="bv-example-row">
      <b-breadcrumb type="light" variant="light">
        <b-breadcrumb-item href="/">
          <b-icon icon="house-fill" scale="1.25" shift-v="1.25" aria-hidden="true"></b-icon>
          Home
        </b-breadcrumb-item>
        <b-breadcrumb-item href="/" active>Foods</b-breadcrumb-item>
      </b-breadcrumb>
      <div class="text-center" style="margin-top:100px; margin-bottom:100px">
            <b-icon icon="emoji-smile" variant="danger" style="width: 70px; height: 70px;" ></b-icon>
            <b-icon icon="emoji-laughing" variant="danger" style="width: 70px; height: 70px;" ></b-icon>
            <b-icon icon="emoji-heart-eyes" variant="danger" style="width: 70px; height: 70px;" ></b-icon>
            <p class="h1">Find Your Favourite Foods</p>
        </div>
      <b-row class="text-center">
        <b-col v-for="(product, i) in filter.meals" :key="i"
          ><b-button
            :to="{
              name: 'Category-list_id',
              params: { id: product.idMeal },
            }"
            style="max-width: 15rem"
            variant="light"
          >
            <b-img :src="product.strMealThumb" style="width: 13rem" rounded alt="Rounded image"></b-img>
            <h5 class="text-center text-dark">
              {{ product.strMeal }}
            </h5>
          </b-button></b-col
        >
      </b-row>
    </b-container>
  </div>
</template>

<script>
import { mapActions, mapState } from "vuex";
import Header from "../../../components/header.vue";
export default {
    async asyncData({ store, params }) {
        await Promise.all([store.dispatch("category/getFilterData", params.name)]);
        return;
    },
    data() {
        return {
            product: [],
        };
    },
    computed: {
        ...mapState("category", {
            filter: (state) => state.filter,
        }),
    },
    methods: {
        ...mapActions("category", ["getFilterData"]),
    },
    components: { Header }
};
</script>
