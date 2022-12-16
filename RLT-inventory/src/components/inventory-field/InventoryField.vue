<template>
    <div class="invetory-window">
        <div class="inventory-fields">

        </div>
        <ModalItemDescription/>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import ModalItemDescription from './modal-item-description/ModalItemDescription.vue'

export default defineComponent({
    components: {
        ModalItemDescription
    },

})
</script>

<style scoped>

</style>