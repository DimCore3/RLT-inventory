<template>
    <div class="character-description">
        <img src="./" alt="">
        <h1> Hero </h1>
        <p> test test test </p>
        <p> test test test </p>
        <p> test test test </p>
        <p> test test test </p>
        <p> test test test </p>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    setup () {
        

        return {}
    }
})
</script>

<style scoped lang="scss">
    .character-description {
        width: 236px;
        height: 464px;
        border: 1px #4D4D4D solid;
        margin: 12px;
        border-radius: 12px;
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 18px 0;

        img { 
            width: 200px;
            height: 240px;
            border-radius: 8px;
        }
    }
</style>