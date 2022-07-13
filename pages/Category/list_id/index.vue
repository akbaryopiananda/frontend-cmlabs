<template>
  <div>
    <Header />
    <div v-for="(product, i) in filter_category.meals" :key="i">
      <b-container>
        <b-breadcrumb type="light" variant="light">
          <b-breadcrumb-item href="/">
            <b-icon icon="house-fill" scale="1.25" shift-v="1.25" aria-hidden="true"></b-icon>
            Home
          </b-breadcrumb-item>
          <b-breadcrumb-item href="/">Foods</b-breadcrumb-item>
          <b-breadcrumb-item href="/">{{ product.strCategory}}</b-breadcrumb-item>
          <b-breadcrumb-item active>{{ product.strMeal }}</b-breadcrumb-item>
        </b-breadcrumb>
      </b-container>
      <div>
        <b-container>
        <h1>{{product.strMeal}}</h1>
        <h5 style="color:red">{{product.strCategory}}</h5>
        <b-row>
          <b-col class="text-center">
            <b-img :src="product.strMealThumb" style="width: 360px" rounded alt="Rounded image"></b-img>
          </b-col>
          <b-col  class="text-justify">
            <div style="margin-bottom:10px">
              <h5>Instruction</h5>
              {{ product.strInstructions }}
            </div>
            <div style="margin-bottom:10px">
            
              <h5>Recipes</h5>
              <li> <b>{{product.strMeasure1}}</b> {{ product.strIngredient1 }} </li>
              <li> <b>{{product.strMeasure2}}</b> {{ product.strIngredient2 }} </li>
              <li> <b>{{product.strMeasure3}}</b> {{ product.strIngredient3 }} </li>
              <li> <b>{{product.strMeasure4}}</b> {{ product.strIngredient4 }} </li>
              <li> <b>{{product.strMeasure5}}</b> {{ product.strIngredient5 }} </li>
              <li> <b>{{product.strMeasure6}}</b> {{ product.strIngredient6 }} </li>
              <li> <b>{{product.strMeasure7}}</b> {{ product.strIngredient7 }} </li>
            </div>
          </b-col>
        </b-row>
        <div class="text-center" style="margin-top:10px; margin-bottom:30px" >
          <div>
            <h1>Tutorial</h1>
          </div>
          <video-player :src="product.strYoutube"/>
        </div>
        </b-container>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions, mapState } from "vuex";
import VideoPlayer from 'nuxt-video-player'

require('nuxt-video-player/src/assets/css/main.css')
export default {
  async asyncData({ store, params }) {
    await Promise.all([
      store.dispatch("category/getFilterCategoryData", params.id),
    ]);
    return;
  },
  components:{
    VideoPlayer
  },
  data() {
    return {
      fields: ["idCategory"],
      product: [],
    };
  },
  computed: {
    ...mapState("category", {
      filter_category: (state) => state.filter_category,
    }),
  },
  methods: {
    ...mapActions("category", ["getFilterCategoryData"]),
  },
};
</script>
