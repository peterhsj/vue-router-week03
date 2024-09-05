<script setup>
  import { ref } from 'vue';

  const imgUrl = ref('https://images.unsplash.com/photo-1558734918-dfc4fe470147?q=80&w=540&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D');

  const num =ref(1);
  const add = () => {
    num.value += 1;
  };
</script>
<template>
  <div class="card">
    <img :src="imgUrl" class="card-img-top" alt="...">
    <div class="card-body">
      <h5 class="card-title">Card title {{ num }}</h5>
      <p class="card-text">aaaaaaa</p>
      <a href="#" class="btn btn-primary" @click.prevent="add">Go somewhere</a>
    </div>
  </div>
</template>