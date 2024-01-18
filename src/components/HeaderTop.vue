<template>
  <div class="header-top">
    <button @click="toggleTheme" class="btn-square" type="button">
      <icon-moon v-if="currentThemeMode" />
      <icon-sun v-if="!currentThemeMode" />
    </button>
    <input
      class="header-top__search"
      ref="inputSearch"
      @keydown.esc="filterKeys = []"
      @keydown.down="toggleFocus"
      @keydown.up="toggleFocus"
      v-model="search"
      @input="handlerSearch"
      placeholder="Введите имя, кличку, город, ресторан и т.п."
      type="text"
    />
    <ul ref="filterBox" v-if="search.length && filterKeys.length" class="filter-box">
      <li v-for="item in filterKeys" :key="item.id">
        <router-link
          @keydown.down="itemFocusDown"
          @keydown.up="itemFocusUp"
          class="filter-box__link"
          :to="item.slug"
          >{{ item.target }} - {{ item.value }}</router-link
        >
      </li>
    </ul>
  </div>
</template>
<script>
import IconMoon from '@/components/icons/IconMoon.vue'
import IconSun from '@/components/icons/IconSun.vue'
import { data } from '@/data.json'

export default {
  components: {
    IconMoon, IconSun
  },
  created() {
    this.data = data
    if (localStorage.getItem('theme-mode')) {
      this.currentThemeMode = localStorage.getItem('theme-mode') === 'light-theme'
      document.documentElement.className = localStorage.getItem('theme-mode')
    }
  },
  mounted() {
    document.addEventListener('click', this.closeFilterBox)
  },
  beforeUnmount() {
    document.removeEventListener('click', this.closeFilterBox)
  },
  data() {
    return {
      currentThemeMode: true,
      filterKeys: [],
      search: '',
      data: [],
      n: 0
    }
  },
  methods: {
    toggleTheme() {
      if (!localStorage.getItem('theme-mode')) {
        localStorage.setItem('theme-mode', 'dark-theme')
        this.currentThemeMode = false
        return
      }
      if (localStorage.getItem('theme-mode') === 'dark-theme') {
        localStorage.setItem('theme-mode', 'light-theme')
        document.documentElement.className = 'light-theme'
        this.currentThemeMode = true
      } else {
        localStorage.setItem('theme-mode', 'dark-theme')
        document.documentElement.className = 'dark-theme'
        this.currentThemeMode = false
      }
    },
    toggleFocus() {
      if (this.search.length && this.filterKeys.length) {
        this.$nextTick(() => {
          this.$refs.filterBox.children[0].children[0].focus()
        })
      }
    },
    closeFilterBox(e) {
      if (!this.filterKeys.length) return
      if (
        e.target.classList.contains('header-top__search') ||
        e.target.classList.contains('filter-box') ||
        e.target.classList.contains('filter-box__link')
      )
        return
      this.filterKeys = []
    },
    itemFocusDown() {
      if (this.search.length && this.filterKeys.length) {
        if (this.n + 1 < this.filterKeys.length) {
          this.n += 1
          this.$nextTick(() => {
            this.$refs.filterBox.children[this.n].children[0].focus({ preventScroll: true })
          })
        }
      }
    },
    itemFocusUp() {
      if (this.search.length && this.filterKeys.length) {
        if (!this.n) {
          this.n -= 1
          this.$nextTick(() => {
            this.$refs.filterBox.children[this.n].children[0].focus()
          })
        }
      }
    },
    handlerSearch() {
      this.filterKeys = []
      if (this.search) {
        this.data.forEach((item) => {
          if (item.target.toLowerCase().includes(this.search.toLowerCase())) {
            this.filterKeys.push(item)
          }
        })
      }
    }
  }
}
</script>
<style lang="scss">
.filter-box {
  position: absolute;
  top: 100%;
  right: 0;
  background-color: var(--color-background-mute);
  max-width: 300px;
  padding: 15px 20px;
  max-height: 300px;
  overflow-y: auto;
  &__link {
    display: block;
    height: 40px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    padding: 10px;
    &:focus {
      background-color: var(--color-background-);
      border-color: var(--color-border);
    }
    @media (hover: hover) {
      &:hover {
        background-color: var(--color-border-hover);
      }
    }
  }
  @media screen and (min-width: 780px) {
    max-width: 500px;
  }
}
.header-top {
  padding: 20px 0;
  display: flex;
  justify-content: space-between;
  position: relative;
  &__search {
    padding: 5px 15px;
    background-color: var(--color-background);
    border-color: var(--color-border);
    color: var(--color-text);
  }
}
.btn-square {
  width: 50px;
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 10px;
  border: 1px solid var(--color-border);
  border-radius: 4px;
  @media (hover: hover) {
    &:hover {
      border-color: var(--color-border-hover);
    }
    &:hover svg {
      transform: rotate(40deg);
    }
  }
  & svg {
    transition: transform 300ms;
  }
}
</style>
