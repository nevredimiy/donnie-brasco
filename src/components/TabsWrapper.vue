<template>
  <div class="tabs">
    <ul class="tabs__header">
      <li
        v-for="title in tabTitles"
        :key="title"
        @click="selectedTitle = title"
        :class="{ selected: title === selectedTitle }"
      >
        {{ title }}
      </li>
    </ul>
    <slot></slot>
  </div>
</template>
<script>
import { ref, provide } from 'vue'
export default {
  setup(props, { slots }) {
    const tabTitles = ref(slots.default().map((tab) => tab.props.title))
    const selectedTitle = ref(tabTitles.value[0])
    provide('selectedTitle', selectedTitle)
    return { tabTitles, selectedTitle }
  }
}
</script>
<style lang="scss">
.tabs {
  &__header {
    display: flex;
    flex-wrap: wrap;
    border-bottom: 1px solid var(--color-border-hover);
    & li {
      padding: 10px 15px;
      border: 1px solid var(--color-border);
      transition: background 300ms;
      cursor: pointer;
      margin-bottom: -1px;
      @media (hover: hover) {
        &:hover {
          border-color: var(--color-border-hover);
        }
      }
    }
  }
  & .selected {
    background-color: var(--color-background-soft);
    border: 1px solid var(--color-border-hover);
    border-bottom: 1px solid var(--color-background-soft);
  }
}
</style>
