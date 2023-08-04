<script setup>
import { computed, ref } from "vue";

const props = defineProps(["class", "color", "backgroundColor", "isDisabled"]);
const hover = ref(false);

const boxShadow = computed(() => {
  return hover.value ? "rgba(0, 0, 0, 0.24) 0px 3px 8px" : "";
});
</script>

<template>
  <button
    class="button"
    @mouseover="hover = true"
    @mouseleave="hover = false"
    :class="class"
    :style="{
      color: !isDisabled ? color : '',
      backgroundColor: !isDisabled ? backgroundColor : '',
      boxShadow,
    }"
    :disabled="isDisabled"
  >
    <slot></slot>
  </button>
</template>

<style lang="scss" scoped>
.button {
  font-size: 11px;
  line-height: 12px;
  letter-spacing: 2.4px;
  text-transform: uppercase;
  padding: 15px 20px;
  box-sizing: border-box;
  border: none;
  cursor: pointer;
  transition: 0.2s;

  &:disabled {
    background-color: dimgrey;
    cursor: not-allowed;
    color: linen;
    opacity: 1;
  }

  @media (min-width: 768px) {
    font-size: 12px;
    padding: 20px 40px;
    width: fit-content;
  }
}
</style>
