<template>
  <table class="m-6 table">
    <thead class="border-2 border-teal-800 bg-gray-400 text-black">
      <tr>
        <th class="border-2 border-teal-800 px-2" scope="col">Date</th>
        <th class="border-2 border-teal-800 px-2" scope="col">Amount</th>
        <th class="border-2 border-teal-800 px-2" scope="col">Category</th>
        <th class="border-2 border-teal-800 px-2" scope="col"></th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(bill, index) in bills" :key="index" class="p-4">
        <td class="border-2 border-teal-800 px-2">{{bill.date | moment("MMM D YYYY")}}</td>
        <td class="border-2 border-teal-800 px-2">${{bill.amount}}</td>
        <td class="border-2 border-teal-800 px-2">{{bill.category}}</td>
        <td class="border-2 border-teal-800 px-2"><button @click="removeBill(index)">𝗫</button></td>
      </tr>
      <tr class="p-4 bg-blue-lighter text-center">
        <td colspan="4"><button class="mt-4 flex-no-shrink p-2 border-2 rounded bg-blue-800 text-white border-teal-800 hover:text-white hover:bg-blue-400" @click="triggerShowAddBill">Add new</button></td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import Moment from "moment";

export default {
  name: 'BillsTable',
  props: ['bills'],
    components: {
        Moment
    },
  methods: {
    triggerShowAddBill: function() {
      this.$emit('triggerShowAddBill')
    },
    removeBill: function(index) {
      this.$emit('removeBill', index)
    }
  }
}
</script>