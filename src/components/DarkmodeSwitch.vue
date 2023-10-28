<script setup>
import { useDark, useToggle } from '@vueuse/core'

const isDark = useDark()
const toggleDark = useToggle(isDark)

var mqList = window.matchMedia('(prefers-color-scheme: dark)');

mqList.addEventListener('change', (event) => {
    toggleDark()
});
</script>

<template>
    <el-button round @click.stop="toggleDark()">DarkMode</el-button>
</template>