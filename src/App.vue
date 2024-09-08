<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="wrapper">
      <nav class="navbar navbar-expand-lg bg-body-tertiary">
        <div class="container-fluid">
          <div class="collapse navbar-collapse justify-content-center" id="navbarNavAltMarkup">
            <div class="navbar-nav">
              <RouterLink to="/" class="nav-link active">Home</RouterLink>
              <RouterLink to="/order" class="nav-link">第三週 作業</RouterLink>
            </div>
          </div>
        </div>
      </nav>
    </div>
  </header>

  <RouterView />
</template>
