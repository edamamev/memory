<script setup>
    import { ref } from 'vue';
    const props = defineProps({
        txt: String,
        id: Number
    })

    const emit = defineEmits(['tool'])
</script>
<template>
    <button @click="emit('tool', props.id)" class="border-none w-32 h-32 bg-background-800 text-text-200 relative rounded-md flex justify-center">
        <p>{{ txt }}</p>
    </button>
</template>
<style>
</style>