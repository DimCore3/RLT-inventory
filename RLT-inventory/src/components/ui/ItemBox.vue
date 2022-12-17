<template>
    <div 
        class="item-box"
        draggable=true
        @dragstart="dragstart"
        @dragend="dragstarted = false"
        :class="{dragstarted: dragstarted}"
        :id="itemProperties.id"
        @click="openModal"
        v-on:click.stop
    >
        <!-- <img :src="itemProperties.img" :alt="itemProperties.name + ' image.'"> -->
        <item-img/>
        <p class="items-amount">{{itemProperties.amount}}</p>
    </div>
</template>

<script lang="ts">
import { toNumber } from '@vue/shared';
import { PropType } from 'vue'
interface itemPropertiesType {
    name: string,
    describe: string,
    amount: number, 
    img: string,
    id: string,
}
export default ({
    name:'item-box',
    data() {
        return {
            dragstarted: false,
        }
    },
    props: {
        itemProperties: {
            type: Object as PropType<itemPropertiesType>,
            required: true,
        },
        index: {
            type: Number,
            required: true,
        }
    },
    methods: {
        openModal() {
            this.$emit('openModal', {itemProperties: this.itemProperties, index:this.index});
        },
        
        dragstart(e:any) {
            e.dataTransfer.effectAllowed = 'move';
            // e.dataTransfer.setData('text/html', this.innerHTML);
            console.log(e)
        }
    }
})
</script>

<style scoped lang="scss">
    .dragstarted {
        border-radius: 12px;
        opacity: 0.4px;
        opacity: 0;
        .items-amount {
            border-bottom-right-radius: 12px;
        }
    }
    .item-box {
        height: 100%;
        width: 100%;
        color: #FFFFFF;

        img {
            height: 48px;
            width: 48px;
        }
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
        position: relative;
        bottom: 17px;
        left: 81px;
    }
</style> 