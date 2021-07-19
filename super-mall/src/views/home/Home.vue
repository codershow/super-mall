<template>
  <div id="home">
    <div class="home-nav">
      <nav-bar>
        <template v-slot:center>
          <div>购物街</div>
        </template>
      </nav-bar>
    </div>
    <home-swiper :banners="banners"></home-swiper>
    <home-recommend-view :recommends="recommends"></home-recommend-view>
    <feature-views></feature-views>
  </div>
</template>

<script>
import NavBar from "@/components/common/navbar/NavBar";
import HomeSwiper from "./childComponents/HomeSwiper";
import HomeRecommendView from './childComponents/HomeRecommendView'
import FeatureViews from './childComponents/FeatureViews'

import { getHomeMultidata } from "@/network/home.js";

export default {
  name: "Home",
  components: {
    NavBar,
    HomeSwiper,
    HomeRecommendView,
    FeatureViews
  },
  data() {
    return {
      banners: [],
      recommends: [],
    };
  },
  created() {
    // 1.请求多条数据
    getHomeMultidata().then((res) => {
      console.log(res);
      this.banners = res.data.banner.list;
      this.recommends = res.data.recommend.list;
    });
  },
};
</script>

<style>
#home {
  padding: 44px 0px 49px 0px;
}

.home-nav {
  background-color: var(--color-tint);
  color: #fff;
  
  position: fixed;
  left: 0;
  top: 0;
  right: 0;
  z-index: 5;
}
</style>