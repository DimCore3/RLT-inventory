<template>
    <div class="modal-item-description">
        <icon-button-close @closeWindow="closeWindow" />
        <div class="item-img-describe">
            <item-img/>
            <!-- <img :src="itemData.img" :alt="itemData.name + ' image'"> -->
        </div>
        <strong> Колличество: {{itemData.amount}}</strong>
        <hr>
        <div class="text-description">
            <h1> {{itemData.name}} </h1>
            <p> {{itemData.describe}} </p>
        </div>
        <div class="delete-item-box">
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
    opacity: 0.95;
    transition: 1s linear;
    strong {
        color:rgb(116, 116, 116);
    };
    
    .item-img-describe {
        width: 130px;
        height: 130px;
    };
}

;

.text-description {
    padding: 6px;
    margin-bottom: 14px;
    height: 30%;
}

;

hr {
    border-bottom: #4D4D4D;
    width: 100%;
    margin-bottom: 16px;
}

.delete-item-box {
    position: sticky;
    top: 100%;
    width: 100%;
    .delete-item-button-box {
        display: flex;
        align-items: center;
    }
}
</style>