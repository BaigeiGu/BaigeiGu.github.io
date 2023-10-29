<script setup>
import { ref, onMounted, computed, toRaw } from 'vue';

import { message } from 'ant-design-vue';

import CharacterCard from './CharacterCard.vue';
import axios from 'axios'

const props = defineProps(['nowlanguage'])
const CharactersData = ref({})

const Characterslist = computed(() => {
    var result = []
    var characters = toRaw(CharactersData.value)['characters']
    var selected = toRaw(SearchValue.value)

    if (CharactersData.value.length == 0 || SearchValue.value.length == 0) {
        result = CharactersData.value['characters']
    }
    else {
        characters.forEach(element => {
            if (element['tags'] != undefined) {
                if (element['tags'].filter(item => selected.includes(item)).length != 0) {
                    result.push(element)
                }
            }
        });
    }
    return result
})

const SearchValue = ref([])
const SearchOptions = computed(() => {
    var cdata = toRaw(CharactersData.value)

    if (CharactersData.value['tags'] == undefined) {
        return []
    }

    var ctags = Object.keys(cdata['tags'])
    var result = ctags.map((e) => ({ label: cdata['tags'][e][props.nowlanguage], value: e }))

    return result
})

function SecrchChange() {

}

onMounted(() => {
    axios.get('/characters.json').then(
        (res) => {
            CharactersData.value = res.data
            if (Object.prototype.toString.call(CharactersData) == '[object Object]') { }
            else {
                message.error('Cannot read data.', 0)
            }
        }
    )
})

</script>
<template>
    <a-select v-model:value="SearchValue" mode="tags" style="width: 100%"
        :placeholder="(props.nowlanguage == 'en') ? 'Filters' : '筛选'" :options="SearchOptions" @change="SecrchChange" allowClear
        showSearch />
    <div class="characters-list">
        <CharacterCard v-for="character in Characterslist" :key="character['id']" v-bind:CharacterCardData="character"
            :nowlanguage="props.nowlanguage" />
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