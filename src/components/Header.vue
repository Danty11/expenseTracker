<template>
  <header>
    <h2>
        EXPENSE TRACKER 
    </h2>
    <div>
        ${{ total }}
    </div>
  </header>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  total:
  {
  type:Number,
  required:true
}
})

</script>

<style scoped>
header{
    
    display: flex;
    background-color: black;
    align-items: center;
    border-bottom: orange solid 5px ;
    justify-content: space-between;
    padding: 10px;
    margin-bottom: 20px ;
}
h2{
  color: orange;
  font-family: sans-serif;
  margin-left: 15px;
  background-color: black ;
}
div{
    color: black;
    margin-right: 25px ;
    background-color:orange ;
    padding: 10px 30px 10px 30px;
    font-size: 20px;
    font-family: sans-serif;
    border:rgb(255, 254, 254) solid 2px ;
    text-align: center;

}
</style>