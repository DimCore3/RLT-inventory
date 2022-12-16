<template>
  <div class="root-app">
    <div class="character-profile">
      <CharacterDescription/>
      <InventoryField/>
    </div>
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
    width: 800px;
  }
  .character-profile {
    display: flex;
    justify-content: space-around;
  }
</style>