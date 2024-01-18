<template>
  <header>
    <header-top />
    <div class="header-main">
      <router-link to="/"><div class="header-main__writer">Джозеф Пистоне</div></router-link>
      <router-link to="/"><h1 class="header-main__title">Донни Браско</h1></router-link>
      <router-link to="/"><div class="header-main__writer">Ричард Вудли</div></router-link>
    </div>
  </header>
</template>
<script>
import HeaderTop from '@/components/HeaderTop.vue'
export default {
  components: {HeaderTop}
}
</script>
<style lang="scss">
.header-main {
  @media only screen and (min-width: 640px) {
    grid-template-columns: 1fr 3fr 1fr;
    &__title {
      font-size: 60px;
    }
  }
  display: grid;
  border-top: 6px solid var(--color-header-border);
  border-bottom: 6px solid var(--color-header-border);
  font-family: Seymourone;
  place-items: center;
  &__title {
    text-align: center;
  }
}
</style>
