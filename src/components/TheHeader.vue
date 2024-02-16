<template>
  <header>
    <header-top />
    <div class="header-main">
      <router-link to="/"><div class="header-main__writer">Джозеф Пистоне</div></router-link>
      <router-link to="/"><h1 class="header-main__title">Донни Браско</h1></router-link>
      <router-link to="/"><div class="header-main__writer">Ричард Вудли</div></router-link>
      <div ref="levsha" class="levsha"></div>
      <div ref="donnie" class="donnie"></div>
    </div>
  </header>
</template>
<script>
import HeaderTop from '@/components/HeaderTop.vue'
export default {
  mounted() {
    setTimeout(() => {
      this.$refs.levsha.classList.add('view-face')
    }, 1000)
    setTimeout(() => {
      this.$refs.donnie.classList.add('view-face')
    }, 500)
  },
  components: { HeaderTop }
}
</script>
<style lang="scss">
.header-main {
  position: relative;
  overflow: hidden;
  
  & .donnie {
    position: absolute;
    top: 0;
    left: 160px;
    width: 220px;
    height: 190px;
    background-image: radial-gradient(rgba(0, 0, 0, 0) 10%, var(--color-background)),
      url('../assets/images/donnie-brasko.png');
    filter: saturate(20%);
    background-position: 20%;
    background-size: contain;
    background-repeat: no-repeat;
    transform: translateY(10%);
    opacity: 0;
    transition:
      transform 1000ms ease-in-out,
      opacity 1000ms ease-in-out;
    z-index: -1;
  }
  & .levsha {
    position: absolute;
    top: -17px;
    right: 170px;
    width: 210px;
    height: 210px;
    background-image: radial-gradient(rgba(0, 0, 0, 0) 10%, var(--color-background)),
      url('../assets/images/levsha.png');
    filter: saturate(20%);
    background-position: 80%;
    background-size: contain;
    background-repeat: no-repeat;
    transform: translateY(-10%);
    opacity: 0;
    transition:
      background-image 300ms ease-in-out,
      transform 1000ms ease-in-out,
      opacity 1000ms ease-in-out;
    z-index: -1;
  }
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
    padding: 0 10px;
  }
  & a {
    transition: scale 300ms;
    position: relative;
  }
  .view-face {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
