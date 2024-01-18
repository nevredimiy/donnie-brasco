<template>
    <article>
        <h2 class="title">
            <slot name="heading"></slot>
        </h2>
        <div class="">Глава семьи: <slot name="head-family"></slot></div>

        <slot></slot>
    </article>
</template>
<script>
export default {

}
</script>
<style>
    article {
        padding: 10px 25px 50px;
    }

</style>