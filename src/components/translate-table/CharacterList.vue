<script setup>
import { ref, onMounted } from 'vue';

import { message } from 'ant-design-vue';

import CharacterCard from './CharacterCard.vue';
import axios from 'axios'

const props = defineProps(['la', 'paw_file'])
var CharactersData = {}
const Characterslist = ref([])

onMounted(() => {
    axios.get('/characters.json').then(
        (res) => {
            CharactersData = res.data
            if (Object.prototype.toString.call(CharactersData) == '[object Object]') { Characterslist.value = CharactersData['data'] }
            else {
                message.error('Cannot read data.',0)
            }
        }
    )
})

</script>
<template>
    <div class="characters-list">
        <CharacterCard v-for="character in Characterslist" :key="character['id']" v-bind:CharacterCardData="character"
            :la="props.la" />
    </div>
</template>
<style scoped>
.characters-list {
    display: grid;
    grid-template-columns: repeat(auto-fill, 18em);
    grid-template-rows: auto;
    justify-content: space-between;
    justify-items: center;
    gap: 1em;
}

@media screen and (max-width: 640px) {
    .characters-list {
        grid-template-columns: repeat(auto-fill, 17em);
    }
}

@media screen and (max-width: 610px) {
    .characters-list {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }
}
</style>