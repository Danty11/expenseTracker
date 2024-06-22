<template>
    <Header :total="total"/>

    <div>

      <AddTransaction @transactionSubmitted="HandleTransaction"/>

      <transactionList :transactions ='transactions' 
      @deleteTransaction="handleTransactionDeletion"/>

    </div>

</template>

<script setup>
import Header from './components/Header.vue';
import AddTransaction from './components/AddTransaction.vue';
import transactionList from './components/transactionList.vue';
import {ref , computed} from 'vue';

const transactions = ref([])

const total = computed(() =>
{
return transactions.value.reduce((asc , transactions) => {
return asc + transactions.price
} , 0)
})


const HandleTransaction = (transactionData) => 
{
transactions.value.push({
  id: crateUniqueId(),
  desc: transactionData.desc,
  price: transactionData.price
})
}



const crateUniqueId = () =>{
  return Math.floor(Math.random() * 10000)
}

const handleTransactionDeletion = (id) =>{
  transactions.value = transactions.value.filter(
    (transaction) => transaction.id !== id
  )
}
</script>




<style  >
*{
  margin: 0;
  background-color: rgb(209, 205, 205) ;
}
</style>
