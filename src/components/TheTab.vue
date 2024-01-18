<template>
  <div class="tab-content" v-show="selectedTitle === title">
    <slot></slot>
  </div>
</template>
<script>
import { inject } from 'vue'
export default {
    props: ["title"],
    setup() {
        const selectedTitle = inject("selectedTitle");
        return {
            selectedTitle
        }
    }
}
</script>
<style lang="scss">
</style>
