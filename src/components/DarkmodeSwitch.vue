<script setup>
import { useDark, useToggle } from '@vueuse/core'

const isDark = useDark()
const toggleDark = useToggle(isDark)


let switchDark = {
    dark: (mediaQueryList) => {
        if (mediaQueryList.matches) {
            toggleDark()
        }
    },
    light: (mediaQueryList) => {
        if (mediaQueryList.matches) {
            toggleDark()
        }
    },
};

window.matchMedia("(prefers-color-scheme: dark)").addListener(switchDark.dark);
window.matchMedia("(prefers-color-scheme: light)").addListener(switchDark.light);
</script>

<template>
    <el-button round @click.stop="toggleDark()">DarkMode</el-button>
</template>