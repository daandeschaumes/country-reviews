<template>
    <div class="o-grid u-grid-main-layout">
        <slot/>
    </div>
</template>
<script>
export default {
    name: "Grid"
}
</script>
<style lang="scss" scoped>
@import '@/assets/style/objects/grid.scss';
@import "@/assets/style/utilities/grid-main-layout.scss";
</style>