<template>
    <div class="item-img-layout">
        <div class="item-layout first-green"></div>
        <div class='item-layout blur-green'></div>
    </div>
</template>

<script lang="ts">
export default ({
    name:'item-img'

})
</script>

<style scoped>
.item-img-layout {
    width: 100%;
    height: 100%;
}
.item-layout {
        width:50%;
        height: 50%;
    }
    .first-green {
        background-color: #7FAA65;
        position: relative;
        left: 26px;
        top: 28px;
        z-index: 1;
    }
    .blur-green {
        background: rgba(184, 217, 152, 0.35);
        position: relative;
        left: 34px;
        bottom: 28px;
        z-index: 2;
        backdrop-filter: blur(5px);
    }
</style>