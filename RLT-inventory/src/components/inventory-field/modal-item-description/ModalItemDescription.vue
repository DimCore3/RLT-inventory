<template>
    <div class="modal-item-description">
        <icon-button-close @closeWindow="closeWindow" />
        <div>
            <img :src="itemData.img" :alt="itemData.name + ' image'">
        </div>
        <hr>
        <div class="text-description">
            <h1> {{itemData.name}} </h1>
            <p> {{itemData.describe}} </p>
        </div>
        <hr>
        <div class="delete-item-button-box">
            <button-action :eventName="'openBoxRemover'" @openBoxRemover="openBoxRemover" v-if="!isRemoverBoxOpen">
                Удалить предмет
            </button-action>

            <SetAmountAndDelete 
                @deleteItems="deleteItems"
                v-model:isRemoverBoxOpen='isRemoverBoxOpen'
                :maxAmount="itemData.amount"
                v-else 
            />
        </div>
    </div>
</template>

<script lang="ts">
import { PropType } from 'vue'
import SetAmountAndDelete from './set-amount-and-delete/SetAmountAndDelete.vue'
interface itemPropertiesType {
    name: string,
    describe: string,
    amount: number,
    img: string,
    id: string,
}
export default ({
    components: {
        SetAmountAndDelete
    },
    props: {
        itemData:{
            type:Object as PropType<itemPropertiesType>,
            required: true,
        }
    },
    data() {
        return {
            isRemoverBoxOpen: false,
        }
    },

    methods: {
        deleteItems(amount: number) {
            this.$emit('deleteItems', amount);
            console.log('Удалено ', amount);
        },
        openBoxRemover(e: boolean) {
            this.isRemoverBoxOpen = e;
        },
        closeWindow() {
            this.$emit('closeWindow');
            console.log('Это окно закроется');
        },
    },
})
</script>

<style scoped lang="scss">
.modal-item-description {
    width: 220px;
    height: 470px;
    padding: 15px;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    position: sticky;
    left: 100%;
    bottom: 100%;
    border: 1px #4D4D4D solid;
    border-top-right-radius: 12px;
    border-bottom-right-radius: 12px;
    background: #262626;
    opacity: 0.97;

    img {
        height: 130px;
        width: 130px;
        margin: 30px 0;
    }
}

;

.text-description {
    padding: 6px;
    margin-bottom: 14px;
    height: 100%;
}

;

hr {
    border-bottom: #4D4D4D;
    width: 100%;
    margin-bottom: 16px;
}

.delete-item-button-box {
    position: sticky;
    top: 100%;
    width: 100%;
    align-items: center;
    display: flex;
}
</style>