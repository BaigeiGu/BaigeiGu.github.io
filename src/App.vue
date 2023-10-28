<script setup>
import TranslateTable from './components/translate-table/TranslateTable.vue';
import 'element-plus/theme-chalk/dark/css-vars.css'
import DarkmodeSwitch from './components/DarkmodeSwitch.vue';

</script>

<template>
    <TranslateTable />
    <el-backtop :right="50" :bottom="50" />
    <DarkmodeSwitch />
</template>

<style scoped></style>
