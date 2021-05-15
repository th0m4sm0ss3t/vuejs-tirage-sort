<template>
  <div class="wrapper">
    <Header />
    <Tirage msg="Bienvenue sur ce site !" />
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Tirage from './components/Tirage.vue';
import Footer from './components/Footer.vue';

export default {
  name: "App",
  components: {
    Header,
    Tirage,
    Footer,
  },
};
</script>

<style lang="scss">
@import './scss/reset.scss';
@import './scss/vars.scss';


#app {
  font-family: 'KoHo', sans-serif;
  background-color: $lightPink;
  font-size: $text-size;
  color: $black;
}

.wrapper {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  justify-content: space-between;
}

</style>
