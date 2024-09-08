<script setup> 
  import { defineProps, defineEmits } from 'vue';
  const props = defineProps(['data']);
  const emit = defineEmits(['selectedItem']);
</script>
<template>
  <div class="list-group">
    <a href="#" v-for="item in data" :key="item.id" @click.prevent="emit('selectedItem', item)" class="list-group-item list-group-item-action">
      <div class="d-flex w-100 justify-content-between">
        <h5 class="mb-1">{{ item.name }}</h5>
        <small> ${{ item.price }}</small>
      </div>
      <p class="mb-1">{{ item.description }}</p>
    </a>
  </div>
</template>