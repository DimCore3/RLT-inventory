<template>
    <div class="bottom-input">
        <icon-button-close></icon-button-close>
        <input type="text" name="" id="" disabled>
    </div>
</template>

<script lang="ts">
export default ({

})
</script>

<style scoped lang="scss">
    .bottom-input {
        height: 40px;
        border: 1px solid #4D4D4D;
        border-radius: 12px;
        padding: 14px;
        margin: 12px;
        background: #262626;
        input {
            border-radius: 12px;
            height: 36px;
            border: none;
            width: 90%;
            background: linear-gradient(90deg, #3C3C3C 0%, #444444 51.04%, #333333 100%);
        }
        button {
            cursor:auto;
        }
    }
</style>