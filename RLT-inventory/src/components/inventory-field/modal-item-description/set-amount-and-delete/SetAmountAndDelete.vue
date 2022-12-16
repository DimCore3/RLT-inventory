<template>
    <div class="box-remover">
        <input-number v-model:amount="amount"></input-number>

        <div class="remover-buttons">
            <button-action :isCancel="true" :eventName="'cancel'" @cancel="cancel">
                Отмена
            </button-action>
            <button-action :eventName="'accept'" @accept="accept">
                Подтвердить
            </button-action>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
export default defineComponent({
    props: {
        maxAmount: {
            type: Number,
            default: 500,
        }
    },
    data() {
        return {
            amount: 0,
        }
    },
    methods: {
        cancel() {
            this.$emit('update:isRemoverBoxOpen', false);
        },
        accept() {
            if (this.amount > this.maxAmount || this.amount <= 0 || this.amount % 1 !== 0) {
                alert('Недопустимое значение');
            } else {
                this.$emit('deleteItems', Math.floor(this.amount));
                this.$emit('update:isRemoverBoxOpen', false);
            }
        },
    }
})
</script>

<style scoped lang="scss">
.box-remover {
    background-color: rgb(97, 97, 97);
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
}

.remover-buttons {
    display: flex;
    width: 100%;
}
</style>