<script setup>
  import AddTransaction from './components/AddTransaction.vue';
  import Balance from './components/Balance.vue';
  import Header from './components/Header.vue';
  import IncomeExpense from './components/IncomeExpense.vue';
  import TransactionList from './components/TransactionList.vue';
  import { ref, computed } from 'vue';

  const transactions = ref([
        {id: 1, text: 'Salary', amount: +7292},
        {id: 2, text: 'Stipend', amount: +6000},
        {id: 3, text: 'Rent', amount: -5500 },
        {id: 4, text: 'Party', amount: -900}
  ])

  const total = computed(() => {
    return transactions.value.reduce((acc, transaction) => {
      return acc + transaction.amount;
    }, 0);
  })

   const income = computed(() => {
    return transactions.value
      .filter((transaction) => transaction.amount > 0)
      .reduce((acc, transaction) => {
        return acc + transaction.amount;
      }, 0)
      .toFixed(2);
   })

   const expenses = computed(() => {
     return transactions.value
      .filter((transaction) => transaction.amount < 0)
      .reduce((acc, transaction) => {
        return acc + transaction.amount;
      }, 0)
      .toFixed(2);
   })
</script>

<template>
  <Header />
  <div class="container">
    <Balance :total = "total" />
    <IncomeExpense :income= "income" :expenses= "expenses" />
    <TransactionList :transactions = "transactions" />
    <AddTransaction />
  </div>
</template>

