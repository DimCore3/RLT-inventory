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
        <img :src="itemProperties.img" :alt="itemProperties.name + ' image.'">
        <p class="items-amount">{{itemProperties.amount}}</p>
    </div>
</template>

<script lang="ts">
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
        border: 1px #4D4D4D solid;
        border-radius: 12px;
        opacity: 0.4px;
        .items-amount {
            border-bottom-right-radius: 12px;
        }
    }
    .item-box {
        height: 100%;
        width: 100%;
        color: #FFFFFF;
        display: flex;
        justify-content: center;
        align-items: center;
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
        position: sticky;
        left: 100%;
        top: 100%;
    }
</style> 