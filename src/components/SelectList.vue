<script setup>
  import { defineProps, defineEmits } from 'vue';
  const props = defineProps(['orders']);
  const emit = defineEmits(['cancelSelector', 'itemSum']); 
</script>
<template>
  <table class="table">
    <thead>
      <tr>
        <th scope="col" width="50">操作</th>
        <th scope="col">品項</th>
        <th scope="col">描述</th>
        <th scope="col" width="90">數量</th>
        <th scope="col">單價</th>
        <th scope="col">小計</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="item in orders" :key="item.id">
        <td><button type="button" class="btn btn-sm" @click="emit('cancelSelector', item.id)">x</button></td>
        <td>{{ item.name }}</td>
        <td><small>{{ item.description }}</small></td>
        <td>
          <select class="form-select" v-model="item.quantity" @click="emit('itemSum', item)">
            <option value="1">1</option>
            <option value="2">2</option>
            <option value="3">3</option>
            <option value="4">4</option>
            <option value="5">5</option>
            <option value="6">6</option>
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
          </select>
        </td>
        <td>{{ item.price }}</td>
        <td>{{ item.total }}</td>
      </tr>
    </tbody>
  </table>
</template>