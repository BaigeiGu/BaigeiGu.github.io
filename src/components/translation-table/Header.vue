<script setup>
const props = defineProps(['nowlanguage'])
const emits = defineEmits(['changeLa'])
const paw_file = { en: 'sibuxiangpaw.png', zh: 'tianlupaw.png' }
</script>
<template>
    <header>
        <img :src="'translation-table/paws/'+paw_file[props.nowlanguage]" class="title-paw" @click="$emit('changeLa')">
        <h1>Youshouyan Translation table</h1>
        <h2>有兽焉译名表</h2>
        <p v-if="nowlanguage == 'en'">This translation table is made for easy communication. Chinese pinyin is preferred for
            translated names.</p>
        <p v-if="nowlanguage == 'zh'">此译名表用于方便交流而制作，点击左侧图片可切换译名，点击右侧文字可复制译名。译名优先使用汉语拼音。</p>
    </header>
</template>

<style scoped>
.title-paw {
    float: right;
    width: 6em;
}

@media screen and (max-width: 370px) {
    .title-paw {
        width: 4em;
    }
}</style>