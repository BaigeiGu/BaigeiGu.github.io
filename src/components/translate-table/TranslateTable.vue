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
    <Header :la="la" @changeLa="changeLa" />
    <Characterslist :la="la"/>
    <Footer :la="la"/>
</template>