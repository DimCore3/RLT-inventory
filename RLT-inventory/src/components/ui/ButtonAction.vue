<template>
    <button 
        @click="click"
        :class="{
            'button-action': !isCancel, 
            'button-cancel': isCancel,
        }"
    >
        <slot></slot>
    </button>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'button-action',
    props: {
        eventName: {
            type: String,
            required: true,
        },
        isCancel: {
            type: Boolean,
            default: false,
        }
    },
    methods: {
        click() {
            this.$emit(this.eventName, true);
        },
    }
})
</script>

<style scoped lang="scss">
    button {
        border-radius: 8px;
        border: none;
        padding: 8px;
        margin: 5px;
        width: 100%;
        transition: 0.1s linear;
    }
    .button-action {
        background: #FA7272;
        color: white;
    }

    .button-action:hover {
        cursor: pointer;
        background: #FF8888;
        transition: 0.1s linear;
    }

    .button-action:active {
        background: #FA7272;
    }

    .button-cancel {
        background: #FFFFFF;
        color: #2D2D2D;
    }

    .button-cancel:hover {
        cursor: pointer;
        background: #ececec;
        transition: 0.1s linear;
    }

    .button-cancel:active {
        background: #FFFFFF;
    }
</style>