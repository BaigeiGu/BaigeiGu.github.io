<script setup>
import { ref } from 'vue';

const la = ref('en')

const paw_file = ref('sibuxiangpaw.png')

function change_la() {
    la.value = (la.value == 'en') ? la.value = 'zh-cn' : la.value = 'en'
    paw_file.value = (la.value == 'en') ? paw_file.value = '/tianlupaw.png' : paw_file.value = '/sibuxiangpaw.png'
}
</script>

<template>
    <header>
        <img :src="paw_file" class="title-paw" @click="change_la">
        <h1>Youshouyan Translation table</h1>
        <h2>有兽焉译名表</h2>
        <p v-if="la == 'en'">This translation table is made for easy communication.
            Chinese pinyin is preferred for translated names.</p>
        <p v-if="la == 'zh-cn'">此译名表用于方便交流而制作，点击左侧图片可切换译名，点击右侧文字可复制译名。译名优先使用汉语拼音。</p>
    </header>
</template>

<style scoped>
header{
    min-height: 12em;
}
h1,
h2 {
    color: #333;
}
.title-paw {
    width: 5em;
    float: right;
}</style>