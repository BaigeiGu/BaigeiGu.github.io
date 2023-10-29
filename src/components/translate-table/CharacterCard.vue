<script setup>
import { ref } from 'vue';
import { message } from 'ant-design-vue';

const props = defineProps({ CharacterCardData: Object, nowlanguage: String })
const name_index = ref(0)
const long_limit = 12

function changeName() { name_index.value = (name_index.value + 1) % props.CharacterCardData['name'].length }
function copyName() {
    var name = props.CharacterCardData['name'][name_index.value]
    navigator.clipboard.writeText(name['zh'] + ' ' + name['en']);
    message.success('Copiled.')
}

</script>
<template>
    <div class="character">
        <img class="character-img" :src="'character-images/' + props.CharacterCardData['image']" @click="changeName" />
        <span class="character-name" @click="copyName">
            <span class="character-name-zh" :class="{
                'character-name-main': (props.nowlanguage == 'zh'),
                'character-name-text': (props.nowlanguage == 'en'),
                'character-name-long': (props.CharacterCardData['name'][name_index]['zh'].length > long_limit)
            }">
                {{ props.CharacterCardData['name'][name_index]['zh'] }}</span>
            <br />
            <span class="character-name-en" :class="{
                'character-name-main': (props.nowlanguage == 'en'),
                'character-name-text': (props.nowlanguage == 'zh'),
                'character-name-long': (props.CharacterCardData['name'][name_index]['en'].length > long_limit)
            }">{{
    props.CharacterCardData['name'][name_index]['en'] }}</span>
        </span>

    </div>
</template>
<style scoped>
.character {
    display: flex;
    height: var(--item-height);
    width: var(--item-width);
    align-items: center;
    border: 1px #d9d9d9 solid;
    border-radius: 1em;
    background-color: rgba(255, 255, 255, .5);
    margin: 1em;
    box-shadow: 0 2px 0 rgba(0, 0, 0, .02);
    transition: all .2s;
    overflow: hidden;
}

.character:hover {
    border-color: #5696a3;
    box-shadow: 0 2px 0 rgba(64, 150, 255, .02);
    transition: all .2s;
}

.character-name {
    transition: all .2s;
}

.character-img {
    height: var(--item-height);
    width: var(--item-height);
    margin-right: 1em;
    transition: all .2s;
    border-radius: 1em 0 0 1em;
    mask-image: radial-gradient(rgba(255, 255, 255, 255)60%, rgba(255, 255, 255, 0) 100%);
    -webkit-mask-image: radial-gradient(rgba(255, 255, 255, 255)60%, rgba(255, 255, 255, 0) 100%);
}


.character:hover .character-img {
    height: calc(var(--item-height) + 2em);
    width: calc(var(--item-height) + 2em);
    transition: all .2s;
}

.character-name {
    opacity: 1;
    transition: opacity .2s;
}

.character-name-main {
    font-size: 1.2em;
    font-weight: 700;
}

.character-name-text {
    font-size: 0.9em;
    font-weight: 400;
}

.character-name-long.character-name-main {
    font-size: 1.1em;
}

.character-name-long.character-name-text {
    font-size: 0.7em;
}

.character-name-zh {
    line-height: 2em;
    transition: all .2s;
}

.character-name-en {
    transition: all .2s;
}

@media screen and (max-width: 640px) {
    .character {
        font-size: 0.8em;
    }
}

@media screen and (max-width: 370px) {
    .character {
        font-size: 0.7em;
    }
}

html.dark .character {
    border: 1px #232323 solid;
    background-color: rgba(255, 255, 255, 0.1);
}
</style>