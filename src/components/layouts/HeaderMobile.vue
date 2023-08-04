<script setup>
import { ref, watch } from "vue";
import logo from "../../assets/logo.svg";

const listItem = [
  { id: 1, title: "Home", href: "#" },
  { id: 2, title: "Galery", href: "#galery" },
  { id: 3, title: "Projects", href: "#projects" },
  { id: 4, title: "Certificates", href: "#certificates" },
  { id: 5, title: "Contacts", href: "#contacts" },
];

const isOpenedMenu = ref(false);

watch(isOpenedMenu, (newVal, oldVal) => {
  if (newVal) {
    document.body.style.overflow = "hidden";
  } else {
    document.body.style.overflow = "auto";
  }
});
</script>

<template>
  <header class="header">
    <nav class="header_navigation">
      <img class="logo" :src="logo" alt="Logo" />

      <div @click="isOpenedMenu = true" class="burger">☰</div>

      <div
        v-if="isOpenedMenu"
        class="blur-background"
        @click="isOpenedMenu = false"
      ></div>

      <Transition>
        <ul
          v-if="isOpenedMenu"
          class="header_navigation__list"
          :class="{ opened: isOpenedMenu }"
        >
          <section class="header_navigation__logo">
            <img class="logo" :src="logo" alt="Logo" />

            <div @click="isOpenedMenu = false" class="burger">✖</div>
          </section>

          <li
            class="header_navigation__list-item"
            v-for="item in listItem"
            :key="item.id"
          >
            <a :href="item.href" @click="isOpenedMenu = false"
              >{{ item.title }}
            </a>
          </li>
        </ul>
      </Transition>
    </nav>
  </header>
</template>

<style lang="scss" scoped>
.header {
  transition: 0.2s ease;

  &_navigation {
    display: flex;
    justify-content: space-between;
    align-items: center;

    &__logo {
      display: flex;
      justify-content: space-between;
      margin-bottom: 20px;
    }

    &__list {
      display: flex;
      position: fixed;
      flex-direction: column;
      padding: 10px 20px;
      background: #fff;
      height: 100vh;
      left: 0;
      right: 0;
      top: 0;
      transition: 0.5s ease;
      width: 280px;
      gap: 10px;
      transform: translateX(0);
      z-index: 2;

      &-item {
        font-size: 16px;
      }
    }
  }
}

.burger {
  font-size: 24px;
  cursor: pointer;
}

.blur-background {
  background-color: rgba(0, 0, 0, 0.502);
  height: 100vh;
  left: 0;
  overflow: hidden;
  position: absolute;
  right: 0;
  top: 0;
  overflow: hidden;
  z-index: 1;
}

a:hover {
  text-decoration: underline;
}

.v-enter-active,
.v-leave-active {
  transition: 0.3s ease;
}

.v-enter-from,
.v-leave-to {
  transform: translateX(-100%);
}
</style>
