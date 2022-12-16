<template>
    <div class="modal-item-description">
        <icon-button-close
            class="modal-exit"
            @closeWindow="closeWindow"
        />
        <img src="" alt="">
        <hr>
        <div class="text-description">
            <h1> test </h1>
            <p> test test test </p>
            <p> test test test </p>
            <p> test test test </p>
            <p> test test test </p>
        </div>
        <hr>

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
        },
        closeWindow() {
            console.log('Это окно закроется')
        },
    },
})
</script>

<style scoped lang="scss">
    .modal-item-description {
        width: 250px;
        height: 500px;
        color: #4D4D4D;
        padding: 15px;
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;
        .modal-exit {
            position: sticky;
            left: 100%;
            bottom: 100%;
        }

        img {
            height: 130px;
            width: 130px;
            margin: 30px 0;
        }
    };
    .text-description {
        padding: 6px;
        margin-bottom: 14px;
    };

    hr {
        border-bottom: #4D4D4D;
        width: 100%;
        margin-bottom: 16px;
    }
</style>