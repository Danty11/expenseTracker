<template>

    <h2>
        ADD TRANSACTION
    </h2>
  <form @submit.prevent="onSubmit">
    <input type="text" class="desc" placeholder="desc..." v-model="desc" >
    <input type="number" class="price" placeholder="enter price (- for negative)" v-model="price">
    <input type="submit" class="submit" value="ADD">
  </form>
</template>

<script setup>
    import {ref} from "vue";

    const desc = ref('')
    const price = ref('')

    const emit = defineEmits(['transactionSubmitted'])

    const onSubmit = () =>
    {
        if(!desc.value || !price.value )
        {
            return
        }
       

        const transactionData = {
            desc:desc.value,
            price:price.value
        }

        emit('transactionSubmitted' , transactionData)

        price.value = ""
        desc.value = ""
    }
</script>

<style scoped>

h2{
    margin-bottom:15px ;
    margin-left: 10px ;
    font-family: sans-serif;
}
form{
    margin-left: 10px ;
    margin-bottom:15px ;
}

input[type=number]::-webkit-inner-spin-button, 
    input[type=number]::-webkit-outer-spin-button { 
    -webkit-appearance: none; 
     margin: 0; 
}

input.desc{
    border-right: none;
    padding-left:5px ;
}
input.price{
    border-left: none;
}
input{
   width: 300px ;
   height: 20px;
   border: orange solid 2px;
   background: rgba(255, 166, 0, 0.651);
   
}
input.submit{
    width: auto;
    height: 26px;
    border-left: none;
    background-color:orange ;
}
input.submit:hover{
    background-color:rgba(255, 166, 0, 0.6) ;
    cursor: pointer;
}
input.submit:active{
    background-color: rgba(233, 153, 3, 0.76) ;
}
input:focus{
   outline: none;
}

</style>