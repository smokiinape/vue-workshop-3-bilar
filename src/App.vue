<script setup>
import { RouterView, RouterLink } from "vue-router"
</script>

<template>
  <header>
    <div class="logo">
      <RouterLink to="/">
        <img
          width="125"
          height="125"
          src="@/assets/logo.jpeg"
        />
      </RouterLink>
    </div>
    <nav>
      <ul>
        <li>
          <RouterLink
            active-class="active"
            to="/"
          >HOME</RouterLink>
        </li>
        <li>
          <RouterLink
            active-class="active"
            to="/about"
          >ABOUT</RouterLink>
        </li>
        <li>
          <RouterLink
            active-class="active"
            to="/cars"
          >CARS</RouterLink>
        </li>
      </ul>
    </nav>
  </header>
  <main>
    <RouterView />
  </main>
</template>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;

  background-color: rgb(0, 0, 0);
  padding: 0px 50px;

  border-bottom: 2px solid white;
  border-top: 2px solid white;
}

ul {
  display: flex;
  justify-content: space-evenly;
  gap: 30px;

  list-style: none;
}

a {
  color: white;
  text-decoration: none;
  font-size: 20px;
}

.active {
  font-weight: bold;
  text-decoration: underline;
}
</style>