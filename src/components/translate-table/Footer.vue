<script setup>
const props = defineProps(['la'])
</script>
<template>
    <p v-if="props.la == 'en'">Data: <a href="/characters.json">characters.json</a></p>
    <p v-if="props.la == 'zh'">数据: <a href="/characters.json">characters.json</a></p>
    <p v-if="props.la == 'en'">Welcome to Youshouyan unofficial Discord Server! <a
            href="https://discord.gg/XEeQCxSr">https://discord.gg/XEeQCxSr</a></p>
    <p v-if="props.la == 'zh'">欢迎加入有兽焉非官方Discord服务器！ <a href="https://discord.gg/XEeQCxSr">https://discord.gg/XEeQCxSr</a>
    </p>
</template>