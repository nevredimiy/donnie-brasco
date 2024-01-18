<template>
  <section>
    <h2 class="section-title">Мафиозные семьи</h2>
    <tabs-wrapper>
      <the-tab title="семья Бонанно">
        <family-item class="tabs__content bonanno" familyName="bonanno">
          <template #heading>Семья Бонанно</template>
          <template #head-family>Кармило Галанте "Лило" - убит в 12 главе</template>
          <div class="">
            Заместитель: Ники Маранджелло (Очкарик Ники, Малыш Ники или Ники Сигары)
          </div>
          <div class="">Расти Растелли - правил семьей после Лило</div>
        </family-item>
      </the-tab>
      <the-tab title="семья Гамбино">
        <family-item class="tabs__content gambino" familyName="gambino">
          <template #heading>Семья Гамбино</template>
          <div class="">Глава семьи: Большой Пол Кастеллано</div>
          <div class="">Заместитель:</div>
        </family-item>
      </the-tab>
      <the-tab title="семья Дженовезе">
        <family-item class="tabs__content genovese" familyName="genovese">
          <template #heading>Семья Дженовезе</template>
          <div class="">Глава семьи: Энтони «Жирный Тони» Салерно</div>
          <div class="">Заместитель:</div>
        </family-item>
      </the-tab>
      <the-tab title="семья Коломбо">
        <family-item class="tabs__content colombo" familyName="colombo">
          <template #heading>Семья Коломбо</template>
          <div class="">Глава семьи: Томми Лабелла</div>
          <div class="">Заместитель:</div>
        </family-item>
      </the-tab>
      <the-tab title="семья Луккезе">
        <family-item class="tabs__content lukese" familyName="lukese">
          <template #heading>Семья Луккезе</template>
          <div class="">Глава семьи: Энтони «Скользкий Тони» Коралло</div>
          <div class="">Заместитель:</div>
        </family-item>
      </the-tab>
    </tabs-wrapper>
  </section>
</template>
<script>
import FamilyItem from './FamilyItem.vue'
import TabsWrapper from './TabsWrapper.vue'
import TheTab from './TheTab.vue'
export default {
  data() {
    return {}
  },
  components: { FamilyItem, TheTab, TabsWrapper },
  methods: {
    handleCLickTab(e) {
      Array.from(this.$refs.tabs.children).forEach((item, idx) => {
        if (item.classList.contains('active')) {
          item.classList.remove('active')
          this.$refs.tabContent.children[idx].classList.remove('active')
        }
      })
      console.log(e.target)
      e.target.classList.add('active')
    }
  }
}
</script>
<style lang="scss">
.tabs {
  &__content {
    background-color: var(--color-background-soft);
  }
}
</style>
