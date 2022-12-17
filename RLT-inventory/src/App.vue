<template>
  <div class="root-app">
    <div class="character-profile">
      <CharacterDescription :character="fullData.character"/>
      <InventoryField :inventoryItems="fullData.items" @deleteItem="deleteItemFromArray" />
    </div>
    <BottomInput />
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
  data() {
    return {
      fullData: {
        character: {
          img: './src/assets/imgBlur.png',
          name: 'name',
          description: 'test test test test test test test test'
        },
        items: [
          {
            name: 'test-name',
            describe: 'test-describe',
            amount: 4,
            img: './',
            id: '123321',
          },
          {
            name: 'test-name-2',
            describe: `test-describe 2
test-describe 2
test-describe 2
test-describe 2
test-describe 2`,
            amount: 2,
            img: './',
            id: '12333',
          },
          {
            name: 'test-name-3',
            describe: 'test-describe 3 test-describe 3 test-describe 3',
            amount: 5,
            img: './',
            id: '1442',
          },
          {},
          {
            name: 'test-name-4',
            describe: `test-describe 4
test-describe 4
test-describe 4`,
            amount: 20,
            img: './',
            id: '1232',
          },
          {},
          {},
        ]
      },
    }
  },
  mounted() {
    this.toFillData();
  },
  methods: {
    toFillData() {
      if (this.fullData.items.length < 25) {
        let toAdd = this.fullData.items.length;
        while (toAdd < 25) {
          toAdd++
          this.fullData.items.push({});
        }
      }
    },
    deleteItemFromArray(index:number) {
      this.fullData.items[index] = {};
    },
  }
})
</script>

<style scoped lang="scss">
.root-app {
  background-color: black;
  height: 660px;
  width: 800px;
}

.character-profile {
  display: flex;
  justify-content: space-around;
}
</style>