<script setup>
    import { ref, watch } from 'vue';

    const props = defineProps({
        minBound: String,
        maxBound: String,
        numRounds: Number,
        multiEncode: Boolean
    })

    const emit = defineEmits(['lowerBound', 'upperBound', 'quantRound', 'multi'])

    const boundMax = ref("10")
    const boundMin = ref("00")
    const roundCount = ref(1)
    const multE = ref(false)

    function leadingZeros(input) {
        if(!isNaN(input.value) && input.value.length === 1) {
        input.value = '0' + input.value;
        }
        return input.value
    }

    defineExpose({
        emitSettings
    })

    function emitSettings(){
        emit('upperBound', boundMax.value)
        emit('lowerBound', boundMin.value)
        emit('quantRound', roundCount.value)
        emit('multi', multE.value)
    }
</script>
<template>
    <div class=" p-7 w-2/3 h-64 bg-accent-200 grid grid-cols-2 gap-5">
        <div class="flex flex-row">
            <label for="inputMin">Min Bound:</label>
            <input type="text" v-model="boundMin" id="inputMin" class=" w-10 h-8">
        </div>
        <div class=" flex flex-row">
            <label for="inputMax">Max Bound:</label>
            <input type="text" v-model="boundMax" id="inputMax" class=" w-10 h-8">
        </div>
        <div class=" flex flex-row">
            <label for="inputRoundCount" >Number of Rounds: </label>
            <input type="number" id="inputRoundCount" v-model="roundCount" class="">
        </div>
        <div class=" flex flex-row ">
            <label for="inputMulti">Multi Encode?</label>
            <input type="checkbox" id="inputMulti" v-model="multE" class="">
        </div>
    </div>
</template>