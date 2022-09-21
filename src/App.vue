<script setup>
  import {ref,computed} from 'vue'
 
  const name="Vue 3"
  
  let cont=ref(0)

  let arrayFavoritos=ref([]);

  const aumentar=()=>cont.value++;

  const disminuir=()=>cont.value--;
  
  const resetear=()=>cont.value=0;

  const add=()=>
  {
    arrayFavoritos.value.push(cont.value);
  }

  const bloquearbtnadd=computed(()=>
  {
    const numsearch=arrayFavoritos.value.find(num=> num===cont.value)
    console.log(numsearch)
    if(numsearch===0) return true
    return numsearch ? true : false
  })
  
  const classCounter=computed(()=>
  {
    if(cont.value===0)
    {
      return 'zero';
    }
    if(cont.value>0)
    {
      return 'positive'
    }
    if(cont.value<0)
    {
      return 'negative'
    }
  })

  
</script>

<template>
  <div class="container text-center">

    <h1>Hola mundo {{name.toUpperCase()}}</h1>
  <h2 :class= "classCounter">{{cont}}</h2>
  <div class="btn-group">
    <button @click="aumentar" class="btn btn-success">Aumentar</button>
  <button @click="disminuir" class="btn btn-danger">disminuir</button>
  <button @click="resetear" class="btn btn-secondary">Resetear</button>
  <button @click="add" :disabled="bloquearbtnadd" class="btn btn-primary">Add</button>
  </div>
  
  

  <ul class="list-group mt-4">
    <li class="list-group-item" v-for="(num,index) in arrayFavoritos" :key="index">
    {{num}}
    </li>
  </ul>

  </div>
  
  
</template>

<style>
  h1{
    color:red;
    }

    .negative
    {
      color: red;
    }
    .positive
    {
      color: green;
    }

    .zero
    {
      color:peru;
    }
</style>