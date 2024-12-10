<script setup>
  import Landing from './components/Landing.vue';
  import MemToolNumbers from './components/MemToolNumbers.vue'
  import { ref, watch } from 'vue';
  const buttons = [
    [1, "Numbers"],
  ]
  const isLandingVisible = ref(true)
  const isNumbersVisible = ref(false)

  let currentTool = 0

  function UpdateCurrentTool(newTool){
    console.log(`newTool: ${newTool}`)
    console.log(`Before: visL: ${isLandingVisible}, visN: ${isNumbersVisible}, cT: ${currentTool}`)
    currentTool = newTool
    console.log(`Before: visL: ${isLandingVisible}, visN: ${isNumbersVisible}, cT: ${currentTool}`)
    switch (newTool){
      case 1:
        isNumbersVisible.value = true;
        isLandingVisible.value = false;
        break;
      case 0:
        isLandingVisible.value = true;
        isNumbersVisible.value = false;
        break;
      default:
        isLandingVisible.value = true;
        isNumbersVisible.value = false;
        break;
    }
    console.log(`Before: visL: ${isLandingVisible}, visN: ${isNumbersVisible}, cT: ${currentTool}`)
  }


</script>

<template>
  <div class="">
    <Landing v-if="isLandingVisible" :buttons="buttons" @tool="(msg) => UpdateCurrentTool(msg)"/>
    <MemToolNumbers v-if="isNumbersVisible" @tool="(msg) => UpdateCurrentTool(msg)"/>
  </div>
</template>
<style>

</style>