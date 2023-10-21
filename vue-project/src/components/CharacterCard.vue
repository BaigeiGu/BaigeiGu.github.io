<script setup>
import { ref } from 'vue'


const props = defineProps({
    Characterdata: { type: Object, required: true }
})

var name_index = ref(0)

function change_name() {
    name_index.value = (name_index.value + 1) % props.Characterdata['name'].length
}

function copy(name) {
    navigator.clipboard.writeText(name['zh'] + ' ' + name['en'])

    ElNotification.success({
        title: 'Success',
        message: 'Copiled.',
    })

}

</script>

<template>
    <div class="character">
        <img class="character-avatar" @click="change_name"
            v-bind:src="'character-images/' + props.Characterdata['image']" />
        <span class="character-name" @click="copy(props.Characterdata['name'][name_index])">
            <span class="character-name-zh">{{ props.Characterdata['name'][name_index]['zh'] }}</span>
            <br />
            <span class="character-name-en">{{ props.Characterdata['name'][name_index]['en'] }}</span>
        </span>

    </div>
</template>

<style scoped>
.character {
    display: flex;
    position: relative;
    height: 5em;
    width: 18em;
    align-items: center;
    border: 1px #d9d9d9 solid;
    border-radius: 1em;
    background-color: rgba(255, 255, 255, 0.5);
    margin: 1em;
    box-shadow: 0 2px 0 rgba(0, 0, 0, 0.02);
    transition: border-color 0.2s;
    overflow: hidden;
}

.character:hover {
    border-color: #4096ff;
    box-shadow: 0 2px 0 rgba(64, 150, 255, 0.02);
    transition: all 0.2s;
}

.character-avatar {
    height: 5em;
    width: 5em;
    margin-right: 1em;
    transition: all 0.2s;
    border-radius: 1em 0 0 1em;
}

.character:hover .character-avatar {
    height: 7em;
    width: 7em;
    transition: all 0.2s;
}

.character-name {
    font-family: var(--fonts-sans);
    white-space: nowrap;
    width: 40em;
    opacity: 1;
    transition: opacity 0.2s;
    user-select: none;
}

.character-name-zh {
    font-size: 0.8em;
    line-height: 2em;
}

.character-name-en {
    font-size: 1.2em;
}


.copy-btn {
    position: absolute;
    height: 2em;
    width: 2em;
    padding: .2em;
    background: rgba(0, 0, 0, 0.03);
    border-radius: 99px;
    left: calc(100% - 2.2em);
    top: calc(100% - 2.2em);
    transition: .2s background;
}


@media screen and (max-width: 768px) {
    .character {
        width: 18em;
    }
}

@media screen and (max-width: 370px) {
    .character {
        width: 16em;
    }
}
</style>
