<template>
  <HeaderVue />
  <div class="container">
    <BalanceVue :total="total" />
    <IncomeExpenses />
    <TransactionListVue :transactions="transactions" />
    <AddTransactionVue />
  </div>
</template>

<script setup lang="ts">
import HeaderVue from "./components/Header.vue";
import BalanceVue from "./components/Balance.vue";
import IncomeExpenses from "./components/IncomeExpenses.vue";
import TransactionListVue from "./components/TransactionList.vue";
import AddTransactionVue from "./components/AddTransaction.vue";

import { ref, computed } from "vue";

const transactions = ref([
      { id: 1, text: 'Flower', amount: -19.99 },
      { id: 2, text: 'Salary', amount: 299.97 },
      { id: 3, text: 'Book', amount: -10 },
      { id: 4, text: 'Camera', amount: 150 },
  ]);

const total = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0);
});
</script>