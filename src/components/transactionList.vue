<template>
      <div class="list">
        <ul>
          <li v-for="transaction in transactions" :key="transaction.id">
            <button @click="deleteTrans(transaction.id)">X</button>
              {{ transaction.desc }} <span>${{ transaction.price }}</span>
          </li>
        </ul>
    </div>
</template>

<script setup>
import {defineProps} from 'vue'

const prop = defineProps ({
    transactions:
    {
        type: Array, 
        require: true
    }
})

const emit = defineEmits(['deleteTransaction'])

const deleteTrans = (id) => {
    emit('deleteTransaction' , id)
};

</script>

<style scoped>

div{
  font-family: sans-serif;
  font-size: 25px;
  
}
ul{
  list-style-type: none;
  margin-left: 10px;
  
}

li{
  background-color:rgb(48, 48, 48) ;
  border:orange solid 3px; 
  padding-top:10px ;
  color: orange;
  width: 614px;
  margin-bottom:10px ;
  
}
span{
  background-color:rgb(48, 48, 48) ;
  color: orange;
  width: 614px;
 
}
button{
  color: rgb(187, 56, 56);
  border: none ;
  padding-bottom:10px ;
  padding-left:15px ;
  padding-right:60px ;
  font-size: 20px;
  
  background-color:rgb(48, 48, 48) ;
}
button:hover{
  color: rgb(255, 0, 0);
  cursor: pointer;
  
}



</style>