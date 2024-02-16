<template>
  <div class="slider">
    <div ref="sliderWrap" class="slider__wrap">
      <div
        :style="`width:${slideWidth}px`"
        v-for="image in imagesList"
        :key="image.id"
        class="slider__item"
      >
        <img :src="image.url" :alt="image.desc" />
      </div>
    </div>
    <button @click="clickPrev" type="button" class="slider__step-icon prev">
      <IconPrev />
    </button>
    <button @click="clickNext" type="button" class="slider__step-icon next">
      <IconNext />
    </button>
    <div class="slider__pagination-bullets">
      <span
        v-for="(_, index) in imagesList"
        :key="index"
        :class="{ active: index === step }"
        class="slider__bullet"
        @click="step = index"
      ></span>
    </div>
  </div>
</template>
<script>
import data from '../assets/imagesList.json'
import IconPrev from './icons/IconPrev.vue'
import IconNext from './icons/IconNext.vue'
export default {
  mounted() {
    this.imagesList = data.data
    this.slideWidth = this.$refs.sliderWrap.offsetWidth
  },
  components: { IconPrev, IconNext },
  data() {
    return {
      imagesList: [],
      slideWidth: 0,
      step: 0
    }
  },
  methods: {
    clickNext() {
      this.step >= this.imagesList.length - 1 ? (this.step = 0) : (this.step += 1)
    },
    clickPrev() {
      this.step <= 0 ? (this.step = this.imagesList.length - 1) : (this.step -= 1)
    }
  },
  watch: {
    step() {
      this.$refs.sliderWrap.style.transform = `translate3d(-${this.step * this.slideWidth}px,0,0)`
    }
  }
}
</script>
<style lang="scss">
.slider {
  position: relative;
  overflow: hidden;
  width: 100%;
  max-height: 600px;
  padding: 30px 0;
  &__wrap {
    height: 100%;
    width: 100%;
    position: relative;
    display: flex;
    align-items: flex-start;
    z-index: 10;
    transform: translate3d(0px, 0, 0);
    transition: transform 300ms ease-in-out;
  }
  &__item {
    flex-shrink: 0;
    backface-visibility: hidden;
    & img {
      width: 100%;
      max-height: 100%;
      -o-object-fit: contain;
      object-fit: contain;
    }
  }
  &__step-icon {
    position: absolute;
    width: 60px;
    color: darkgrey;
    z-index: 20;
    top: 50%;
    transform: translateY(-50%);
    background-color: rgba($color: #000000, $alpha: 0.2);
    border-radius: 2px;
    display: flex;
    justify-content: center;
    align-items: center;
    transition:
      color,
      background-color,
      400ms ease-in-out;
    @media (hover: hover) {
      &:hover {
        background-color: gray;
        color: #fff;
      }
    }
  }
  & .prev {
    left: 20px;
  }
  & .next {
    right: 20px;
  }
  &__pagination-bullets {
    position: absolute;
    bottom: 10px;
    text-align: center;
    z-index: 20;
    width: 100%;
    background-color: rgba($color: #fff, $alpha: 0.2);
    & .active {
      background-color: rgba($color: #000000, $alpha: 0.3);
    }
  }
  &__bullet {
    width: 10px;
    height: 10px;
    background-color: darkgray;
    border-radius: 50%;
    display: inline-block;
    margin: 0 4px;
    border-color: rgba(0, 0, 0, 0.3);
    // box-shadow: 0 0 5px rgba($color: #ffffff, $alpha: 0.5);
    border-width: 1px;
    border-style: solid;
    cursor: pointer;
  }
}
</style>
