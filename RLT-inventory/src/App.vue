<template>
  <div class="root-app">
    <icon-button-close/>
    <item-box
      :itemProperties="{
        name: 'test-name',
        describe: 'test-describe',
        amount: 4, 
        img: './',
        id: '123321',
      }"
    ></item-box>
    <CharacterDescription/>
    <InventoryField/>
    <BottomInput/>
  </div>
</template>

<script lang="ts">
import BottomInput from './components/bottom-input/BottomInput.vue';
import InventoryField from './components/inventory-field/InventoryField.vue'
import CharacterDescription from './components/character-description/CharacterDescription.vue';
export default ({
  components: {
    BottomInput,
    InventoryField,
    CharacterDescription,
  },
})
</script>

<style scoped lang="scss">
  .root-app {
    background-color: #262626;
    height: 660px;
    width: 90%;
  }
</style>