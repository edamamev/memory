<script setup>
    import { ref } from 'vue'
    import Nav from './Nav.vue'
    import ToolDisplayText from './ToolDisplayText.vue';
    import ToolTitle from './ToolTitle.vue';
    import ToolSettingsNumber from './ToolSettingsNumber.vue';
    import ToolButton from './ToolButton.vue';
    import ToolInput from './ToolInput.vue';

    const emit = defineEmits(['tool'])
    const inSettings = ref(true)
    const inEncode = ref(false)
    const inDecode = ref(false)
    const inReview = ref(false)

    const displayNumber = ref("295730")
    const buttonText = ref("Ready?")

    function DetermineButtonFunction(){
        if (inSettings.value){
            FromSettingsToEncode()
        } else if (inEncode.value){
            FromEncodeToDecode()
        } else if (inDecode.value){
            // When we get to having several numbers at the same time,
            // this'll be important for swapping between Encoding and Decoding
            FromDecodeToReview()
        } else if (inReview.value){
            FromReviewToSettings()
        }
    }

    function FromSettingsToEncode(){
        inSettings.value = false
        inEncode.value = true
        buttonText.value = "Encoded"
    }

    function FromEncodeToDecode(){
        inEncode.value = false
        inDecode.value = true
        buttonText.value = "Submit"
    }

    function FromDecodeToReview(){
        inDecode.value = false
        inReview.value = true
        buttonText.value = "Done"
    }

    function FromReviewToSettings(){
        inReview.value = false
        inSettings.value = true
        buttonText.value = "Ready?"
    }

</script>
<template>
    <div class="">
        <Nav @tool="(msg) => emit('tool', msg)" />
        <!--Main Application Below-->
        <div class="bg-background-400 min-h-screen min-w-full flex justify-center items-center">
            <!--Container?-->
            <div class=" container flex flex-col bg-secondary-800 justify-center items-center">
                <ToolTitle v-if="inSettings" txt="Number Rapscallion Training"/>
                <ToolSettingsNumber v-if="inSettings" />
                <ToolDisplayText v-if="inEncode" :txt="displayNumber"/>
                <ToolInput v-if="inDecode" />
                <ToolButton :txt="buttonText" @click="DetermineButtonFunction()"/>
            </div>
        </div>
    </div>
</template>
<style>
</style>the