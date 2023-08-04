<script setup>
import HeaderMobile from "./HeaderMobile.vue";
import HeaderDesktop from "./HeaderDesktop.vue";
import { useMediaQuery } from "@vueuse/core";

const isLargeScreen = useMediaQuery("(min-width: 1024px)");
</script>

<template>
  <HeaderMobile v-if="!isLargeScreen" />

  <HeaderDesktop v-else />
</template>

<style lang="scss" scoped></style>
