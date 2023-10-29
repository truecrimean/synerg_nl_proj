<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <aside class="left-menu">
    <img alt="Synergy logo" class="logo" src="@/assets/sinergy-project-logo.svg" width="163" height="91" />
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
  font-size: 16px;
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
