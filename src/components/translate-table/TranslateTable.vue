<script setup>
import Header from './Header.vue';
import Characterslist from './CharacterList.vue';
import Footer from './Footer.vue';


import { ref } from 'vue';

const la = ref('en')

function changeLa() {
    la.value = (la.value == 'en') ? 'zh' : 'en'
}


</script>
<template>
    <div class="TranslateTable">
        <Header :la="la" @changeLa="changeLa" />
        <a-divider />
        <Characterslist :la="la" />
        <a-divider />
        <Footer :la="la" />
    </div>
</template>

<style scoped>
.TranslateTable {
    padding: 5em;
}

@media screen and (max-width: 768px) {
    .TranslateTable {
        padding: 3em;
    }
}

@media screen and (max-width: 690px) {
    .TranslateTable {
        padding: 1em;
    }
}
</style>

<style>
:root {
    --item-height: 6em;
    --item-width: 18em;
    --name-font-size-en: 1.2em;
    --name-font-size-zh: 0.8em;
}

@media screen and (max-width: 370px) {
    :root {
        --item-width: 17em;
    }
}
</style>