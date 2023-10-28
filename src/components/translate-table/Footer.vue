<script setup>
const props = defineProps(['la'])
</script>
<template>
    <div v-if="props.la == 'en'" class="en">
        <p>Data: <a href="/characters.json">characters.json</a></p>
        <p>Welcome to Youshouyan unofficial Discord Server! <a
                href="https://discord.gg/XEeQCxSr">https://discord.gg/XEeQCxSr</a></p>
    </div>
    <div v-if="props.la == 'zh'" class="zh">
        <p>数据: <a href="/characters.json">characters.json</a></p>
        <p>欢迎加入有兽焉非官方Discord服务器！ <a href="https://discord.gg/XEeQCxSr">https://discord.gg/XEeQCxSr</a>
        </p>
    </div>
</template>