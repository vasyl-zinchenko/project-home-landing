<script setup>
import { ref } from "vue";
import logo from "../../assets/logo.svg";

const listItem = [
  { id: 1, title: "Home", href: "#" },
  { id: 2, title: "Galery", href: "#galery" },
  { id: 3, title: "Projects", href: "#projects" },
  { id: 4, title: "Certificates", href: "#certificates" },
  { id: 5, title: "Contacts", href: "#contacts" },
];

const currentTab = ref("");
</script>

<template>
  {{ currentTab }}
  <header class="header">
    <nav class="header_navigation" id="home">
      <img class="logo" :src="logo" alt="Logo" />

      <ul class="header_navigation__list">
        <li
          class="header_navigation__list-item"
          v-for="item in listItem"
          :key="item.id"
          @click="currentTab = item.title"
        >
          <a
            :style="currentTab === item.title ? { fontWeight: 'bold' } : {}"
            :href="item.href"
            >{{ item.title }}</a
          >
        </li>
      </ul>
    </nav>
  </header>
</template>

<style lang="scss" scoped>
.header {
  transition: 0.2s ease;

  &_navigation {
    display: grid;
    grid-template-columns: 1fr 2fr;

    &__logo {
      display: flex;
      margin-bottom: 20px;
    }

    &__list {
      display: flex;
      justify-content: start;
      align-items: center;
      padding: 10px 20px;
      transition: 0.5s ease;
      gap: 60px;
      transform: translateX(0);
      text-transform: uppercase;

      @media (min-width: 1024px) {
        padding: 0;
      }

      &-item {
        font-size: 12px;
        line-height: 12px;
        letter-spacing: 2.4px;
        text-transform: uppercase;
      }
    }
  }
}

a {
  line-height: initial;
  &::after,
  &::before {
    display: block;
    content: "";
    height: 1px;
    background-color: black;
    width: 0;
    transition: 0.2s;
  }

  &::before {
    margin-bottom: 3px;
  }

  &:hover::after,
  &:hover::before {
    width: 100%;
  }
}
</style>
