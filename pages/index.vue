<script>
import axios from "axios";
export default {
  // async asyncData(){
  //   const res = await axios.get("https://vue-lessons-api.herokuapp.com/photo/list"
  //   );
  //   console.log(res);
  //   return { res: res.data };
  //   },
    data() {
      return {
        res:[]
      };
    },
    async fetch(){
       this.res = await axios
       .get("https://vue-lessons-api.herokuapp.com/photo/list")
       .then(res => res.data);
    },
      activated() {
      // Call fetch again if last fetch more than 30 sec ago
      if (this.$fetchState.timestamp <= Date.now() - 10000) {
        this.$fetch()
      }
    },
  };
</script>

<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">Cyn</h1>
      <h1 v-if="$fetchState.pending">Loading...</h1>
      <h1 v-if="$fetchState.error"> ERROR {{ $fetchState.error }}</h1>
      <img v-for="item in res" :key="item.url" :src="item.url" alt="">
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          rel="noopener noreferrer"
          class="button--green"
        >
          Documentation
        </a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          rel="noopener noreferrer"
          class="button--grey"
        >
          GitHub
        </a>
      </div>
    </div>
  </div>
</template>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
