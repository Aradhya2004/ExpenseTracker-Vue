<script setup>
  import AddTransaction from './components/AddTransaction.vue';
  import Balance from './components/Balance.vue';
  import Header from './components/Header.vue';
  import IncomeExpense from './components/IncomeExpense.vue';
  import TransactionList from './components/TransactionList.vue';
  import { ref } from 'vue';

  const transactions = ref([
        {id: 1, text: 'Salary', amount: +7292},
        {id: 2, text: 'Stipend', amount: +6000},
        {id: 3, text: 'Rent', amount: -5500 },
        {id: 4, text: 'Party', amount: -900}
    ])
</script>

<template>
  <Header />
  <div class="container">
    <Balance />
    <IncomeExpense />
    <TransactionList :transactions = "transactions" />
    <AddTransaction />
  </div>
</template>

