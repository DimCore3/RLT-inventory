<template>
    <button @click="closeWindow">
        X
    </button>
</template>

<script lang="ts">
export default ({
    name:'icon-button-close',
    methods: {
        closeWindow() {
            this.$emit('closeWindow', true);
        }
    }
})
</script>

<style scoped lang="scss">
    button {
        background-color: rgba($color: #000000, $alpha: 0.0);
        height: 12px;
        width: 12px;
        border: none;
        color: white;
        text-align: center;
        font-size: smaller;
    }

    button:hover {
        cursor: pointer;
    }
</style>