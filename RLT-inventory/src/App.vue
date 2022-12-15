<template>
  <div>
    <button-action :eventName="'fff'" @fff="clickFff"> 
      Удалить предмет
    </button-action>

    <button-cancel> Cancel </button-cancel>
    <icon-button-close/>
    <input-number></input-number>
    <item-box></item-box>
  </div>
</template>

<script lang="ts">
export default ({
  data() {
    return {

    }
  },
  methods:{
    clickFff(e:boolean) {
      console.log(e);
    }
  },
})
</script>

<style scoped lang="scss">

</style>