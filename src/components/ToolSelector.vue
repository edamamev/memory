<script setup>
    import ToolSelectorButton from './ToolSelectorButton.vue'

    const props = defineProps({
        buttons: Array,
    })

    const emit = defineEmits(['tool'])

</script>
<template>
    <div class="container flex justify-evenly gap-3 bg-primary-800 p-10">
        <ToolSelectorButton @tool="(msg) => emit('tool', msg)" :txt="buttons[0][1]" :id="buttons[0][0]" />
    </div>
</template>
<style>
</style>