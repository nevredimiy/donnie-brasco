<template>
     <section>
        <h2 class="section-title">Локации</h2>
        <div class="">Выберите главу и следите за перемещением героев книги на карте</div>
        <tabs-wrapper>
            <the-tab title="Глава1"><h2 class="title">Квартира Донни Браско</h2></the-tab>
            <the-tab title="Глава2">2</the-tab>
            <the-tab title="Глава3">3</the-tab>
            <the-tab title="Глава4"><h2 class="title">клуб Гиппопотам</h2></the-tab>
            <the-tab title="Глава5">5</the-tab>
            <the-tab title="Глава6">6</the-tab>
            <the-tab title="Глава7">7</the-tab>
            <the-tab title="Глава8">8</the-tab>
            <the-tab title="Глава9">9</the-tab>
            <the-tab title="Глава10">10</the-tab>
            <the-tab title="Глава11">11</the-tab>
            <the-tab title="Глава12">12</the-tab>
            <the-tab title="Глава13">13</the-tab>
            <the-tab title="Глава14">14</the-tab>
            <the-tab title="Глава15">15</the-tab>
            <the-tab title="Глава16">16</the-tab>
            <the-tab title="Глава17">17</the-tab>
        </tabs-wrapper>
     </section>
</template>
<script>
import TabsWrapper from './TabsWrapper.vue';
import TheTab from './TheTab.vue';
export default {
    components: { TheTab, TabsWrapper }
}
</script>