<script setup>
import {ref, computed} from 'vue'

const titulo = "Contador de números dinámico!"
const styleColor = "color:brown"
const contador = ref(0)
const arrayFavoritos = ref([])


const increment = () => {
  contador.value++
}
const decrement = () => {
  contador.value--
}
const reset = () => {
  contador.value = 0
}
const add = () =>{
  arrayFavoritos.value.push(contador.value)
}
const bloquearBtnAdd = computed(() =>{
  const numSearch = arrayFavoritos.value.find((num) => num === contador.value)
    if (numSearch === 0){
        return true}
  return numSearch ? true : false;
})


const counterColor = computed( () =>{
  if (contador.value ===  0){
    return 'zero'
  }else if(contador.value > 0){
    return 'positive'
  }else if(contador.value < 0){
    return 'negative'
  }
})


</script>
<template>
<div class="container text-center mt-5">
  <h1 :style="styleColor">{{titulo}}</h1>
  <h2 :class="counterColor">{{ contador }}</h2>
  <br>
  <div>
  <button @click="increment" class="btn btn-aumentar">Aumentar</button>
  <button @click="decrement" class="btn btn-decrementar">Decrementar</button>
  <button @click="reset"class="btn btn-resset">Resset</button>
  <button @click="add" :disabled="bloquearBtnAdd" class="btn btn-add">Add</button>
  </div>
  <br>
  <ul>
    <li v-for="(num, index) in arrayFavoritos" :key="index">
      {{ num }}
    </li>
  </ul>
</div>
</template>





<!--estilos-->
<style >
  body{
    background-color: rgb(206, 206, 211);
  }
  .zero{
    color:orange;
  }
  .positive{
    color:green;
  }
  .negative{
    color:red;
  }
  ul{
    list-style: none;
  }
  .btn-aumentar{
    background-color: #7393A7;
    border-color: #7393A7;
    color: white;
  }
  .btn-aumentar:hover{
    background-color: #b5cfd8;
    border-color: #b5cfd8;
  }
  
    .btn-decrementar{
    background-color: #7393A7;
    border-color: #7393A7;
    color: white;
  }
  .btn-decrementar:hover{
    background-color: #b5cfd8;
    border-color: #b5cfd8;
  }
  
    .btn-resset{
    background-color: #7393A7;
    border-color: #7393A7;
    color: white;
  }
  .btn-resset:hover{
    background-color: #b5cfd8;
    border-color: #b5cfd8;
  }
  
    .btn-add{
    background-color: #7393A7;
    border-color: #7393A7;
    color: white;
  }
  .btn-add:hover{
    background-color: #b5cfd8;
    border-color: #b5cfd8;
  }
  #app {
  width: 100%;
  min-height: 100vh;
}
  
</style>
