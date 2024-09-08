<script setup>
  import { defineProps } from 'vue';
  const props = defineProps(['orderList']);
</script>

<template>
  <table class="table">
    <thead>
      <tr>
        <th scope="col">品項</th>
        <th scope="col">數量</th>
        <th scope="col">小計</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="item in orderList.order" :key="item.id">
        <td>{{ item.name }}</td>
        <td>{{ item.quantity }}</td>
        <td>{{ item.total }}</td>
      </tr>
    </tbody>
  </table>
  <div class="text-end">備註: <span>{{ orderList.note }}</span></div>
  <div class="text-end">
    <h5>總計: <span>${{ orderList.total }}</span></h5>
  </div>
</template>