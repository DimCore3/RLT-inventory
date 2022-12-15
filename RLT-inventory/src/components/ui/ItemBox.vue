<template>
    <div 
        class="item-box" 
        :id="itemProperties.id"
        @click="openModal"
    >
        <img :src="itemProperties.img" :alt="itemProperties.name + ' image.'">
        <p class="items-amount">{{itemProperties.amount}}</p>
    </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'

interface itemPropertiesType {
    name: string,
    describe: string,
    amount: number, 
    img: string,
    id: string,
}

export default defineComponent({
    name:'item-box',
    props: {
        itemProperties: {
            type: Object as PropType<itemPropertiesType>,
            required: true,
        }
    },
    methods: {
        openModal() {
            console.log('open modal');
            this.$emit('openModal', this.itemProperties);
        }
    }
})
</script>

<style scoped lang="scss">
    .item-box {
        height: 100px;
        width: 100px;
        color: #FFFFFF;
        border: 1px #4D4D4D solid;
    }

    .item-box:hover {
        cursor: pointer;
    }
    .items-amount {
        border: 1px solid #4D4D4D;
        border-top-left-radius: 6px;
        height: 16px;
        width: 16px;
        text-align: center;
        position: sticky;
        left: 100%;
        top: 100%;
    }
</style> 