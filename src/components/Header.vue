<template>
  <header class="header">
      <h1 class="header__title">Tirage au sort</h1>
      <!--<p class="header__text">{{ message }}</p>-->
  </header>
</template>

<script>
export default {
    name: 'Header',
    props: {
        message: String,
    }
}
</script>

<style lang="scss">
@import '../scss/vars.scss';

.header {
    padding: $gutter;
    background-color: $hotPink;

    &__title {
        margin: $gutter 0;
        font-family: 'Bangers', sans-serif;
        font-size: $title-size;
        text-align: center;
        text-transform: uppercase;
        color: $white;
    }

    &__text {
        text-align: center; 
        margin: $gutter 0;
    }
}

</style>