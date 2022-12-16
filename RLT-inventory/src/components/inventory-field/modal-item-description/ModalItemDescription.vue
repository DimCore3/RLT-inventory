<template>
    <div class="modal-item-description">
        <img src="" alt="">
        <br>
        <h1> test </h1>
        <p> test test test </p>
        <br>

        <button-action :eventName="'openBoxRemover'" @openBoxRemover="openBoxRemover" v-if="!isRemoverBoxOpen">
            Удалить предмет
        </button-action>

        <SetAmountAndDelete @deleteItems="deleteItems" v-model:isRemoverBoxOpen='isRemoverBoxOpen' v-else />
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import SetAmountAndDelete from './set-amount-and-delete/SetAmountAndDelete.vue'

export default defineComponent({
    components: {
        SetAmountAndDelete
    },

    data() {
        return {
            amount: 0,
            isRemoverBoxOpen: false,
        }
    },

    methods: {
        deleteItems(amount: number) {
            console.log('Удалено ', amount)
        },
        openBoxRemover(e: boolean) {
            this.isRemoverBoxOpen = e;
            console.log(e);
        }
    },
})
</script>

<style scoped lang="scss">
    .modal-item-description {
        width: 250px;
        height: 500px;
    }
</style>