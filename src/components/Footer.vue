<template>
    <footer class="footer">
       <p class="footer__text">Réalisé par <a href="https://github.com/th0m4sm0ss3t" target="_blank" class="footer__link">Thomas Mosset</a>. (2021)</p>
    </footer>
</template>

<script>
export default {
    name: "Footer",

}
</script>

<style lang="scss">
@import '../scss/vars.scss';

.footer {
    margin-top: $gutter;
    padding: $gutter;
    color: $white;
    background-color: $hotPink;
    display: flex;
    justify-content: center;

    &__link {
        font-weight: bold;
        color: $white;
        text-decoration: none;

        &:hover {
            color: $black;
        }
    }
}


</style>