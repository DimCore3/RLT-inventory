<template>
    <div class="invetory-window">
        <div 
            class="inventory-field" 
            v-for="(container, index) in inventoryItems" 
            :id="'cont-' + index" 
            :key="'cont-' + index"
        >
            <item-box v-if="JSON.stringify(container) != '{}'"
            :itemProperties="{
                name: container.name,
                describe: container.describe,
                amount: container.amount, 
                img: container.img,
                id: container.id,
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
    props: {
        inventoryItems: {
            type: Array,
            default: [],
        }
    },
    mounted() {
        this.createGrid();
    },
    methods: {
        createGrid() {

        }
    }

})
</script>

<style scoped>
    .invetory-window {
        width: 500px;
        height: 500px;
        border: 1px #4D4D4D solid;
        margin: 12px;
        border-radius: 12px;
        background: #262626;
        display: flex;
        flex-wrap: wrap;
        align-content: flex-start;
    }
    .inventory-field {
        height: 98px;
        width: 98px;
        border: 1px #4D4D4D solid;
    }
</style>