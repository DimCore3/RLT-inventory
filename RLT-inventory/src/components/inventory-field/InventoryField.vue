<template>
    <div class="invetory-window" @click="isModalOpen = true ? false : true">
        <div 
            class="inventory-field" 
            v-for="(itemData, index) in inventoryItems" 
            :id="'cont-' + index"
            :key="'cont-' + index"
            :class="{isModalOpened:isModalOpen}"
        >
            <item-box 
                v-if="JSON.stringify(itemData) != '{}'" 
                :id="'item-' + index" 
                :key="'item-' + index"
                :index="index"
                :itemProperties="itemData" 
                @openModal="openModal"
            >
            </item-box>
        </div>
        <ModalItemDescription 
            v-if="isModalOpen" 
            :itemData="modalData" 
            @click.stop
            @deleteItems="deleteItems"
            @closeWindow="isModalOpen = false"
             
        />
    </div>
</template>

<script lang="ts">
interface itemPropertiesType {
    name: string,
    describe: string,
    amount: number,
    img: string,
    id: string,
};
interface itemPropsWithIndex {
    itemProperties: itemPropertiesType,
    index: number,
}
import ModalItemDescription from './modal-item-description/ModalItemDescription.vue'
export default ({
    components: {
        ModalItemDescription
    },
    props: {
        inventoryItems: {
            type: Array,
            default: [],
        }
    },
    data() {
        return {
            isModalOpen: false,
            indexOpenedItem: 0,
            modalData: {
                name: '',
                describe: '',
                amount: 0,
                img: '',
                id: '',
            },
        }
    },
    methods: {
        openModal(itemData:itemPropsWithIndex) {
            this.isModalOpen = !this.isModalOpen
            this.modalData = itemData.itemProperties;
            this.indexOpenedItem = itemData.index;
            console.log(this.modalData)
        },
        deleteItems(amount: number) {
            this.modalData.amount = this.modalData.amount - amount;
            if (!this.modalData.amount) {
                this.isModalOpen = false;
                this.$emit('deleteItem',this.indexOpenedItem);
            }
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
    height: 99px;
    width: 99px;
    border-right: 1px #4D4D4D solid;
    border-bottom: 1px #4D4D4D solid;
}

.isModalOpened {
    filter:blur(3px);
}
</style>