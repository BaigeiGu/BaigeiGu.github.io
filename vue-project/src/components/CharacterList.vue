<script setup>
import { ref } from 'vue'
import CharacterCard from './CharacterCard.vue'
import axios from 'axios'

var character_data = {}
var character_list = ref([])

function updateData() {
    axios.get('/characters.json').then((res) => {
        character_data = res.data
        character_list.value = character_data['data']
    })
}
updateData()
</script>

<template>
    <div class="characters-list">
        <div v-for="character in character_list" :key="character.id">
            <CharacterCard v-bind:Characterdata="character" />
        </div>
    </div>
    <!-- <button class='refresh_btn' @click="updateData">Refresh</button> -->
</template>

<style>
.characters-list {
    display: grid;
    grid-template-columns: repeat(auto-fill, 20em);
    grid-template-rows: auto;
    justify-content: space-between;
    justify-items: center;
}

@media screen and (max-width: 768px) {
    .characters-list {
        font-size: 0.8em;
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }
}

@media screen and (max-width: 370px) {
    .characters-list {
        font-size: 0.7em;
    }
}

.refresh_btn {
    font-size: 1em;
    padding: 1em;
    background-color: #fff;
    border: 1px solid rgba(0, 0, 0, .12);
    border-radius: .4em;
    align-items: center;
    cursor: pointer;
    margin: 1em;
    margin-bottom: 0;
    transition: border-color .2s;
}

.refresh_btn:hover {
    border-color: #4096ff;
    transition: border-color .2s;
}
</style>
