<template>
    <button>
        <slot></slot>
    </button>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name:'button-cancel',
    setup () {
        

        return {}
    }
})
</script>

<style scoped lang="scss">

</style>