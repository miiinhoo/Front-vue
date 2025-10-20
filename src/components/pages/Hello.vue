<template>
  
</template>
<script setup>



  // ------------------------

  const prop = defineProps({
    num: Number,
    update: Number,
    reset: Number,
  });
  const emit = 
  defineEmits([
    'update:num',
    'update:update',
    'update:reset'
  ]);

  function firstNumber(data){
    emit('update:one',Number(data));
  }
  
</script>