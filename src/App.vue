<template>
  <Header/>
  <div class="container">
    <Balance/>
    <incomeExpenses/>
    <TransactionList/>
    <AddTransaction/>
  </div>

</template>


<script>
import Header from './components/Header.vue'
import Balance from "./components/Balance.vue";
import incomeExpenses from "./components/IncomeExpenses.vue";
import TransactionList from "./components/TransactionList.vue";
import AddTransaction from "./components/AddTransaction.vue";
export default {
  components: {
    Header,
    Balance,
    incomeExpenses,
    TransactionList,
    AddTransaction
  }
}
</script>