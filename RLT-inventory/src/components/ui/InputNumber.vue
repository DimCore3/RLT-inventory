<template>
    <input 
        type="number"
        placeholder="Введите количество"
        @input="inputAmount"
    >
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent ({
    name:'input-number',
    props: {

    },
    methods: {
        inputAmount(e:any) {
            this.$emit('update:amount',e.target.value);
        }
    }
})
</script>

<style scoped lang="scss">
    input {
      height: 40px;
      width: 100%;
      border: 1px #4D4D4D solid;
      border-radius: 4px;
      padding: 0px 12px;
      margin: 5px;
      background-color: rgba($color: #000000, $alpha: 0.0);
      color: white;
    };

    input::-webkit-outer-spin-button,
    input::-webkit-inner-spin-button {
        -webkit-appearance: none;
        margin: 0;
    }
</style>