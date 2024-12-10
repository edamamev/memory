<script setup>
    import ToolSelector from './ToolSelector.vue'

    const props = defineProps({
        buttons: Array
    })
    
    const emit = defineEmits(['tool'])
</script>
<template>
    <div class="container min-h-screen min-w-full flex flex-col justify-center items-center bg-primary-800">
        <h1 class="w text-text-200">Edme's Memory Tools</h1>
        <!--Tools-->
        <ToolSelector :buttons="buttons" @tool="(msg) => emit('tool', msg)" />
    </div>
</template>