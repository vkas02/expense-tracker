<template>
  <Header/>
  <div class="container">
    <Balance :total="+total"/>
    <incomeExpenses :income="+income" :expenses="+expenses"/>
    <TransactionList :transactions="transactions" @transcationDeleted ="handleTransactionDeleted"/>
    <AddTransaction @transcationSubmitted="handleTranscationSubmitted"/>
  </div>

</template>


<script setup>
import Header from './components/Header.vue'
import Balance from "./components/Balance.vue";
import incomeExpenses from "./components/IncomeExpenses.vue";
import TransactionList from "./components/TransactionList.vue";
import AddTransaction from "./components/AddTransaction.vue";
import {useToast} from "vue-toastification";
import {ref,computed, onMounted} from "vue";


const toast= useToast()

const transactions = ref([])

onMounted(()=>{
  const savedTranscations= JSON.parse(localStorage.getItem('transactions'));
  if(savedTranscations){
    transactions.value=savedTranscations;
  }
})

const total= computed(()=>{
  return transactions.value.reduce((acc,transaction)=>{
    return acc+transaction.amount;
  },0)
})

const income=computed(()=>{
  return transactions.value
      .filter((transaction)=>transaction.amount>0)
      .reduce((acc,transaction)=>{
        return acc+transaction.amount;
      },0).toFixed(2)
})
const expenses=computed(()=>{
  return transactions.value
      .filter((transaction)=>transaction.amount<0)
      .reduce((acc,transaction)=>{
        return acc+transaction.amount;
      },0).toFixed(2)
})
const handleTranscationSubmitted=(transactionData)=>{
  transactions.value.push({
    id:generateUniqueId(),
    text:transactionData.text,
    amount:transactionData.amount,
  });
  saveTransactionToLocalStorage();
  toast.success('Transaction Added')
}
const generateUniqueId=()=>{
  return Math.floor(Math.random()*10000)
}
const handleTransactionDeleted=(id)=>{
  transactions.value=transactions.value.filter((transaction)=>
  transaction.id!==id)
  saveTransactionToLocalStorage();
  toast.success('Transaction deleted')
}

const saveTransactionToLocalStorage=()=>{
  localStorage.setItem('transactions',JSON.stringify(transactions.value));
}

</script>