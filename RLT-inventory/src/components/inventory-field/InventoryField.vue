<template>
    <div class="invetory-window">
        <div class="inventory-fields">
            <item-box
            :itemProperties="{
                name: 'test-name',
                describe: 'test-describe',
                amount: 4, 
                img: './',
                id: '123321',
            }"
            ></item-box>
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
    .invetory-window {
        width: 525px;
        height: 500px;
        border: 1px #4D4D4D solid;
        margin: 12px;
        border-radius: 12px;
    }
</style>