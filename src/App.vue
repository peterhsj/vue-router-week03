<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="wrapper">
      <nav>
        <RouterLink to="/">Home</RouterLink> |
        <!-- <RouterLink to="/about">About</RouterLink> | -->
        <RouterLink to="/order">第三週 作業</RouterLink> |
      </nav>
    </div>
  </header>

  <RouterView />
</template>
