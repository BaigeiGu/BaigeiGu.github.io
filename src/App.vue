<script setup>
import TranslateTable from './components/translation-table/TranslationTable.vue';
import DarkmodeSwitch from './components/DarkmodeSwitch.vue';
import Theme from './antd-theme.json';

</script>

<template>
    <a-config-provider :theme="Theme">
        <TranslateTable />
    </a-config-provider>
    <DarkmodeSwitch />
    <a-back-top />
</template>

<style scoped></style>
