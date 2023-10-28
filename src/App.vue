<script setup>
import TranslateTable from './components/translate-table/TranslateTable.vue';
import DarkmodeSwitch from './components/DarkmodeSwitch.vue';
import { theme } from 'ant-design-vue';
import Theme from './theme.json'
</script>

<template>
    <a-config-provider :theme="Theme">
        <TranslateTable />
    </a-config-provider>
    <DarkmodeSwitch />
    <a-back-top />
</template>

<style scoped></style>
