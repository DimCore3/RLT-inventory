<template>
    <div class="character-description">
        <img :src="character.img" alt="character image">
        <h1> {{character.name}} </h1>
        <p> {{character.description}} </p>
    </div>
</template>

<script lang="ts">
interface characterType {
    img: string,
    name: string,
    description: string,
};
import { PropType } from 'vue'
export default ({
    props: {
        character: {
            type: Object as PropType<characterType>,
            required: true,
        }
    }
})
</script>

<style scoped lang="scss">
    .character-description {
        width: 236px;
        height: 464px;
        border: 1px #4D4D4D solid;
        margin: 12px;
        border-radius: 12px;
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 18px 0;
        background: #262626;

        img { 
            width: 200px;
            height: 240px;
            border-radius: 8px;
        }
    }
</style>