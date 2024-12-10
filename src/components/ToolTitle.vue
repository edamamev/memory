<script setup>
    const props = defineProps({
        txt: String
    })
</script>
<template>
    <div>
        <h1 class=" text-text-100">{{ txt }}</h1>
    </div>
</template>