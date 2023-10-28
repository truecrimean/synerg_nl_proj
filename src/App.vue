<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <aside class="left-menu">
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />
    <div class="wrapper">
      <nav>
        <RouterLink to="/">Главная</RouterLink>
        <RouterLink to="/favorite">Избранное</RouterLink>
      </nav>
    </div>
  </aside>
  <main class="main">
    <RouterView />
  </main>
</template>

<style scoped>
aside {

}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: block;
  padding: 0 1rem;
}
</style>
