<script setup>
  import { defineProps, defineEmits } from 'vue';

  defineProps(['cardContent'])

  // 定義要 emit 的名稱
  const emit = defineEmits(['emitTitle']);
  // 1.執行 editOutTitle 發動一個名為 emitTitle 的 emit 將資料送出
  const editOutTitle = () => {
    // 2.參數只能傳一個
    emit('emitTitle', '圖片')
  };
</script>
<template>
  <div class="card">
    <img :src="cardContent.imgUrl" class="card-img-top" alt="...">
    <div class="card-body">
      <h5 class="card-title">{{ cardContent.title }}</h5>
      <p class="card-text">{{ cardContent.content }}</p>
      <input type="text" >
      <a href="#" class="btn btn-primary" @click.prevent="emit('emitTitle', cardContent.title)">傳遞事件</a>

    </div>
  </div>
</template>