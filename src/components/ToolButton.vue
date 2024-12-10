<script setup>
    const props = defineProps({
        txt: String
    })

    const emit = defineEmits(['click'])
</script>
<template>
    <button @click="emit('click', true)" class="border-none p-5 bg-primary-600 hover:bg-primary-500 text-text-100 rounded-md">
        {{ txt }}
    </button>
</template>