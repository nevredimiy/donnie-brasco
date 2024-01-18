<template>
  <div class="container sticky">
    <nav  class="menu">
      <ul ref="list" class="list">
        <li @click="handleDropdown" class="item">
          Содержание
          <ul class="dropdown">
            <li class="item"><a href="/">1. И грянул гром</a></li>
          </ul>
        </li>
        <li @click="handleDropdown" class="item">
          Мафиозные семьи
          <ul class="dropdown">
            <li class="item"><a href="#family-bonanno">семья Бонанно</a></li>
            <li class="item"><a href="#family-gambino">семья Гамбино</a></li>
            <li class="item"><a href="#family-genovese">семья Дженовезе</a></li>
            <li class="item"><a href="#family-colombo">семья Коломбо</a></li>
            <li class="item"><a href="#family-lukese">семья Луккезе</a></li>
          </ul>
        </li>
        <li @click="handleDropdown" class="item">Локации
          <ul class="dropdown">
            <li class="item"><a href="#appartment-donny">Квартира Донни</a></li>
            <li class="item"><a href="#ranbow-room">Рэйнбоу рум</a></li>
            <li class="item"><a href="#carmelo">ресторан Кармелло</a></li>
            <li class="item"><a href="#gipopotam">клуб Гиппопотам</a></li>
            <li class="item"><a href="#akerg">АКЕРГ</a></li>
            <li class="item"><a href="#u-igorya">У Игоря</a></li>
            <li class="item"><a href="#holiday">Холидей</a></li>
            <li class="item"><a href="#bus-stop">Бас стоп</a></li>
            <li class="item"><a href="#wolk-gvido">Поездка с Гвидо</a></li>
            <li class="item"><a href="#toilend">Тойленд</a></li>
            <li class="item"><a href="#casa-bella">Каса белла</a></li>
            <li class="item"><a href="#shato-madrid">Шато Мадрид</a></li>
            <li class="item"><a href="#holiday-bar">Холидэй Бар</a></li>
          </ul>
        </li>
      </ul>
    </nav>
  </div>
</template>
<script>
export default {
  data() {
    return {}
  },
  mounted() {
    window.document.addEventListener('click', this.closeDropуMenu)
  },
  beforeUnmount() {
    window.document.removeEventListener('click', this.closeDropуMenu)
  },
  methods: {
    closeDropуMenu(e) {
      if (!this.$refs.list.contains(e.target)) {
        Array.from(this.$refs.list.children).forEach(item => {
          item.children[0].classList.remove('active')
        })
      }
    },
    handleDropdown(event) {
      const menu = document.querySelector('.list')
      Array.from(menu.children).forEach((item) => {
        if (item.children[0].classList.contains('active')) {
          item.children[0].classList.remove('active')
        }
      })
      event.target.children[0].classList.toggle('active')
    }
  }
}
</script>

<style lang="scss">
.sticky{
  position: sticky;
  top:0;
  z-index: 30;
}
.menu {
  margin: 15px 0;
  background-color: var(--color-background);
}
.list {
  display: flex;
  gap: 15px;

  & > .item {
    position: relative;
    border: 1px solid var(--color-border);
    border-radius: 5px;
    padding: 10px 5px;
    font-weight: 600;
    cursor: pointer;
    transition:
      color 300ms,
      background 300ms,
      text 300ms;
    @media (hover: hover) {
      &:hover {
        border-color: var(--color-border-hover);
        background-color: var(--color-background-mute);
        color: var(--vt-c-text-light-2);
      }
    }
    & a {
      padding: 10px 15px;
    }
  }
}
.dropdown {
  display: none;
  position: absolute;
  z-index: 30;
  top: 100%;
  left: 0;
  background-color: #fff;
  margin-top: 5px;
  padding: 10px 15px;
  border-radius: 10px;
  min-width: 180px;
  width: max-content;
  box-shadow:
    10px 10px 20px rgba(0, 0, 0, 0.5),
    1px 1px 5px rgb(255, 255, 255);
  color: #000;
  @media (hover: hover) {
    & > .item:hover {
      background-color: var(--vt-c-text-dark-2);
    }
  }
}
.active {
  display: block;
}
</style>
