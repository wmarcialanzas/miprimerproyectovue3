<script setup>
import {ref,computed} from "vue";

const name = "vue dinamico";
const counter = ref(0);
const arrayfavoritos = ref([])

const increment =()=>{
  counter.value++;
};

const decrement =()=>{
  counter.value--;
};
const reset =()=>{
  counter.value=0;
};

const add=()=>{

  arrayfavoritos.value.push(counter.value)
}

const bloquearbtn = computed (()=>{
const numsearch =arrayfavoritos.value.find(num=>num===counter.value)
console.log(numsearch)
//if (numsearch===0) return true;
//return numsearch ? true:false;
return numsearch||numsearch===0
})

const classcounter =computed(() => {
if (counter.value===0) {

  return "zero";
}

if (counter.value>0){

  return "positive";
}

if(counter.value<0){

  return "negative";
}

}


)


</script>


<template>
<div class="container text-center mt-3">
  <h2 :class="classcounter">{{ counter }}</h2>

  <div class="btn-group">
    <button @click="increment" class="btn btn-success">increment</button>
    <button @click="decrement" class="btn btn-danger">decrement</button>
    <button @click="reset" class="btn btn-secondary">reset</button>
    <button @click="add" :disabled="bloquearbtn" class="btn btn-primary">Add</button>
  </div>
 
  <ul class="list-group mt-4">
  <li v-for="(num,index) in arrayfavoritos" :key="index" class="list-group-item"> {{ num }} </li>
  </ul>
</div>
</template>


<style>

.positive {

color:green;

}

.negative{

  color:red;

}

.zero {
color:peru;

}
</style>