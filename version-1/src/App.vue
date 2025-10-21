<script setup>
  import { ref } from 'vue';
  import Hello from './components/pages/Hello.vue';

  //-----------------
  const firstNumber = ref('');
  const secondNumber = ref('');
  const operatorList = ["+","-","÷","x","x²"]
  const op = ref('');

  const currentInput = ref('firstNumber'); // 초기값 지정

  

  function updateNumber(num){
    if(currentInput.value === "firstNumber") firstNumber.value += num;
    else secondNumber.value += num;
  }
  function resetBtn(){
    firstNumber.value = '';
    secondNumber.value = '';
    equal.value = '';
    op.value="";
    currentInput.value = 'firstNumber';
  }
  function updateOperator(oper){
    currentInput.value = 'secondNumber';
    op.value="";
    op.value = oper;
    console.log(oper)
  }
  
  const equal = ref('');
  function addEqaul(x){
    const a = Number(firstNumber.value);
    const b = Number(secondNumber.value);
    const currentOp = op.value;
    const temp = () => {
      switch(currentOp){
      case "+":
        return a + b;
      case "-":
        return a - b;
      case "÷":
        if(b === 0){
          alert("0으로는 나눌 수 없습니다.")
          return 0;
          }
      return a / b;
      case 'x':
        return a * b;
      case "x²":
        return Math.pow(a,b);
      default:
        return '';
    }
    
    }
    equal.value = '= ' + temp();
  }
</script>

<template>
  <Hello
    v-model:num="firstNumber"
    v-model:num2="secondNumber"
    v-model:update="updateNumber"
    v-model:reset="resetBtn"
  />
  <div class="number">
    {{ firstNumber }} {{ op }} {{ secondNumber }} {{  equal  }}
  </div>
  <div class="button-wrapper">
    <button v-for="n in 9" :key="n"
    :class="`btn`+n"
    @click="updateNumber(n)">
        {{ n }}
    </button>
    <button v-for="operation in operatorList" :key="op"
    class="oper"
    @click="updateOperator(operation)">
      {{ operation }}
    </button>
    <button @click="addEqaul(e)" class="oper">
      =
    </button>
    <div>
    <button @click="resetBtn()" class="reset">
      초기화
    </button>
  </div>
  </div>

  


</template>

<style scoped lang="scss">
 *{ margin:0; padding: 0;}
 body{
  width: 100vw;
  height: 100vh;
 }
 
 li{list-style: none;}
 a{text-decoration: none;color: inherit;}
 .number{
  margin:0 auto;
  width: 40%;
  height: 15%;
  font-size: 2rem;
  text-align: center;
  line-height: 7rem;
  background-color: whitesmoke;
  border: 1px solid gray;
  border-radius: 50px;
 }
 .button-wrapper{
  box-sizing: border-box;
  padding: 10px;
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  width: 40%;
  height: 55%;
  border: 1px solid;
  border-radius: 5%;
  position: absolute;
  top:50%;left:50%;
  transform: translate(-50%,-50%);
  @for $buttons from 1 through 9{
    .btn#{$buttons}{
      width: calc((100% - 80px) / 3);
    }
  }

    .oper{
      width: calc((100% - 50px) / 7);
    }
    .reset{
      width: 100px;
      height: 40px;
    }
 }
 
</style>
