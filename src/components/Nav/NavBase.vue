<script setup>
import { RouterLink } from "vue-router";

const options = [
  { name: "Home" },
  { name: "Resumen" },
  { name: "About" },
];
</script>

<template>
  <nav>
    <RouterLink
      v-for="({ name }, index) in options"
      :key="index"
      :to="{ name }"
      active-class="active"
    >
      {{ name }}
    </RouterLink>
  </nav>
</template>

<style lang="scss">
nav {
  display: flex;
  justify-content: space-around;
  padding: 10px 0 15px;
  border-bottom: 1px solid #2e2e2e;

  a {
    color: #2e2e2e;
    text-decoration: none;
  }

  a.active {
    font-weight: bold;
  }
}
</style>
