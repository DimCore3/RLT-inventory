<template>
  <div>
    <button-action :eventName="'fff'" @fff="clickFff"> 
      Удалить предмет
    </button-action>
    <icon-button-close/>
    <input-number
      v-model:amount="amount"
    ></input-number>
    <item-box></item-box>
  </div>
</template>

<script lang="ts">
export default ({
  data() {
    return {
      amount:0,
    }
  },
  methods:{
    clickFff(e:boolean) {
      console.log(e);
      console.log(this.amount)
    }
  },
})
</script>

<style scoped lang="scss">

</style>