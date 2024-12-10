<script setup>
    const emit = defineEmits(['tool'])
</script>
<template>
    <button @click="emit('tool', 0)" class="">BACK to LANDING</button>
</template>
<style>
</style>