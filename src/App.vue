<script setup>
  import { ref } from 'vue';
  import Hello from './components/pages/Hello.vue';

  //-----------------
  const number = ref('');

  function updateNumber(num){
    number.value += num;
  }
  function resetBtn(){
    number.value = '';
  }
</script>

<template>
  <Hello
    v-model:num="number"
    v-model:update="updateNumber"
    v-model:reset="resetBtn"
  />

  <p>
    <br>
    테스트
    <br>
    결과 : {{ first }} {{ operator }} {{ second }} = {{ operEqaul() }}
  </p>


</template>

<style scoped>

</style>
