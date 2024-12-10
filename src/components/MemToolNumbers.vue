<script setup>
    const emit = defineEmits(['tool'])
</script>
<template>
    <div class="bg-background-100">
        <button @click="emit('tool', 0)">BACK to LANDING</button>
        <h1>BWA</h1>
    </div>
</template>
<style>
</style>