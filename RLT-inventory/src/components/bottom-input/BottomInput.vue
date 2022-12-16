<template>
    <div class="bottom-input">
        <icon-button-close></icon-button-close>
        <input type="text" name="" id="" disabled>
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
    .bottom-input {
        height: 40px;
        border: 1px solid #4D4D4D;
        border-radius: 12px;
        padding: 14px;
        margin: 12px;
        background: #262626;
        input {
            border-radius: 8px;
            height: 36px;
            border: none;
            width: 90%;
        }
    }
</style>