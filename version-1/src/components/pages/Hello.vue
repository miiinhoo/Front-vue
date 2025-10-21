<template>
  <div>
    <button v-for="value in source"></button>
  </div>
</template>
<script setup>



  // ------------------------

  const prop = defineProps({
    num: Number,
    num2: Number,
    update: Number,
    reset: Number,
    btn:Array,
  });
  const emit = 
  defineEmits([
    'update:num',
    'update:num2',
    'update:update',
    'update:reset',
    'update:btn'
  ]);

  
  
</script>