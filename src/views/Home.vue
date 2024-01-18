<template>
  <the-header />
  <mafia-families />
  <the-location />
  <main class="container">
    <div class="circle-menu">
      <div @click="isActive = !isActive" class="circle-menu__boss">Джилли</div>
      <div v-if="isActive" class="circle-menu__desc">
        занимаеться краденным барахлом. На лет 5 старше Донни. Среднего роста, веса и телосложения,
        с темными волосами и горбатым носом. Держит магазин на 76-йстрит в Бенсонхерсте - АКЕРГ. В
        дальнейшем солдат семьи Коломбо
      </div>
      <ul>
        <li></li>
      </ul>
    </div>
  </main>
  <h1>Home page</h1>
</template>
<script>
import TheHeader from '../components/TheHeader.vue'
import FamilyItem from '../components/FamilyItem.vue'
import MafiaFamilies from '../components/MafiaFamilies.vue'
import TheLocation from '../components/TheLocation.vue'

export default {
  components: { TheHeader, TheHeader, FamilyItem, MafiaFamilies, TheLocation },

  data() {
    return {
      isActive: false
    }
  }
}
</script>

<style lang="scss">
.circle-menu {
  display: grid;
  place-content: center;
  height: 300px;
  position: relative;
  z-index: 10;
  &__boss {
    font-weight: 600;
    display: flex;
    justify-content: center;
    align-items: center;
    border: 1px solid var(--color-border);
    border-radius: 50%;
    width: 100px;
    height: 100px;
    cursor: pointer;
    transition:
      background 300ms,
      color 300ms;
    @media (hover: hover) {
      &:hover {
        background-color: var(--color-background-mute);
        color: var(--vt-c-text-light-2);
      }
    }
  }
  &__desc {
    position: absolute;
    max-width: 400px;
    border: 1px solid var(--color-border);
    border-radius: 10px;
    box-shadow:
      0 0 15px rgba(0, 0, 0, 0.4),
      2px 2px 5px rgb(255, 255, 255);
    padding: 10px;
    left: 60%;
  }
}
</style>
