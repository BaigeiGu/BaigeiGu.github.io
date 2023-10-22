<script setup>
import { ref } from 'vue';
const props = defineProps({ CharacterCardData: Object })
const name_index = ref(0)

function changeName() { name_index.value = (name_index.value + 1) % props.CharacterCardData['name'].length }
function copyName(name) {
    navigator.clipboard.writeText(name['zh'] + ' ' + name['en']); ElNotification({
        title: 'Success',
        message: 'Copiled.',
        type: 'success'
    })
}

</script>
<template>
    <div class="character">
        <img class="character-img" :src="'character-images/' + props.CharacterCardData['image']" @click="changeName" />
        <span class="character-name" @click="copyName(props.CharacterCardData['name'][name_index])">
            <span class="character-name-zh">{{ props.CharacterCardData['name'][name_index]['zh'] }}</span>
            <br />
            <span class="character-name-en">{{ props.CharacterCardData['name'][name_index]['en'] }}</span>
        </span>

    </div>
</template>
<style scoped>
.character {
    display: flex;
    height: 6em;
    width: 18em;
    align-items: center;
    border: 1px #d9d9d9 solid;
    border-radius: 1em;
    background-color: rgba(255, 255, 255, .5);
    margin: 1em;
    box-shadow: 0 2px 0 rgba(0, 0, 0, .02);
    transition: border-color .2s;
    overflow: hidden;
}

.character:hover {
    border-color: #4096ff;
    box-shadow: 0 2px 0 rgba(64, 150, 255, .02);
    transition: all .2s;
}

.character-name {
    transition: transform .2s;
}

.character-img {
    height: 6em;
    width: 6em;
    margin-right: 1em;
    transition: all .2s;
    border-radius: 1em 0 0 1em;
}


.character:hover .character-img {
    height: 8em;
    width: 8em;
    transition: all .2s;
}

.character-name {
    font-family: var(--fonts-sans);
    white-space: nowrap;
    opacity: 1;
    transition: opacity .2s;
}

.character-name-zh {
    font-size: 0.8em;
    line-height: 2em;
}

.character-name-en {
    font-size: 1.2em;
    font-weight: 700;
}

@media screen and (max-width: 640px) {
    .character {
        font-size: 0.8em;
    }
}

@media screen and (max-width: 370px) {.character {
        width: 17em;
        font-size: 0.7em;
    }
}

</style>