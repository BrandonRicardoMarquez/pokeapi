<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
<header>
  <nav class="navbar navbar-expand-lg bg-dark narbar-dark">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">
      <img alt="Vue logo" 
        class="logo" 
        src="@/assets/logo.svg" 
        width="100" 
        height="44" 
      />
    </a>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <RouterLink to="/" class="btn btn-outline-primary me-2">Home  </RouterLink>
        </li>
        <li class="nav-item dropdown">
          <RouterLink to="/about" class="btn btn-outline-danger me-2">About  </RouterLink>
          <!-- <ul class="dropdown-menu">
            <li><a class="dropdown-item" href="#">Action</a></li>
            <li><a class="dropdown-item" href="#">Another action</a></li>
            <li><hr class="dropdown-divider"></li>
            <li><a class="dropdown-item" href="#">Something else here</a></li>
          </ul> -->
        </li>
        <li class="nav-item">
          <RouterLink to="/Pokemons" class="btn btn-outline-warning">Pokemons</RouterLink>
        </li>
      </ul>
      <form class="d-flex" role="search">
        <input class="form-control me-10" type="search" placeholder="Search" aria-label="Search" >
        <button class="btn btn-outline-success" type="submit" @click="getData(data.name)" :to="`/pokemons/pikachu`">Search</button>
      </form>
    </div>
  </div>
  </nav>
</header>
  <!-- <header>
    <img alt="Vue logo" 
    class="logo" 
    src="@/assets/logo.svg" 
    width="125" 
    height="125" 
    />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/Pokemons">Pokemons</RouterLink>
      </nav>
    </div>
  </header> -->
<br>
<div class="container">
  <RouterView />
</div>
</template>

<!-- <style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
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
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style> -->
