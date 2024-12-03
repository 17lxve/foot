<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="wrapper">
      <nav class="navbar">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">Classement</RouterLink>
      </nav>
    </div>
  </header>
<Suspense>
  <RouterView />
</Suspense>

</template>

<style scoped>
.wrapper {
  width: 100%;
  aspect-ratio: 18/1;
  display: flex;
  flex-direction: row;
  gap: 20%;
  background-color: orange;
  align-items: center;
  justify-content: center;
  border-radius: 2rem;
  margin-bottom: 1rem;
}
.navbar {
  display: inherit;
  gap: 20%;
}

a {
  text-decoration: none;
  font-size: xx-large;
  color: var(--text);
  font-weight: bolder;
}
</style>
