<script setup>
import { computed, ref, watch } from "vue";
import slide1 from "../assets/slider/slide-1.png";
import slide2 from "../assets/slider/slide-2.png";
import { useElementSize } from "@vueuse/core";
import BaseButton from "./ui/BaseButton.vue";

const el = ref(null);
const { height } = useElementSize(el);

const dummyHeight = ref(null);

watch(height, (newHeight) => {
  if (newHeight > 0) {
    dummyHeight.value = newHeight;
  }
});

const slides = ref([
  {
    id: 1,
    img: slide1,
  },
  {
    id: 2,
    img: slide2,
  },
]);

const isSlideShown = ref(true);
const slidesLength = computed(() => slides.value.length);
const slideNumber = ref(1);

const switchSlide = (value) => {
  value === "next" ? (slideNumber.value += 1) : (slideNumber.value -= 1);
  isSlideShown.value = false;
  setTimeout(() => {
    isSlideShown.value = true;
  }, 0);
};
</script>

<template>
  <div class="slider" id="galery">
    <h1 class="headline headline__mobile">
      <span class="headline__first-part">PROJECT</span
      ><span class="headline__second-part">HOME</span>
    </h1>

    <section class="slide" :style="{ height: dummyHeight + 'px' }">
      <div>
        <Transition>
          <img
            ref="el"
            v-if="isSlideShown"
            :src="slides[slideNumber - 1].img"
            alt=""
          />
        </Transition>

        <BaseButton
          class="slide__view"
          :color="'#333'"
          :backgroundColor="'white'"
        >
          VIEW →
        </BaseButton>
      </div>
    </section>

    <section class="controls">
      <h1 class="headline headline__desktop">
        <span class="headline__first-part">PROJECT</span
        ><span class="headline__second-part">HOME</span>
      </h1>

      <section class="controls__arrows">
        <button
          class="controls__arrow"
          @click="switchSlide('prev')"
          :disabled="slideNumber === 1"
        >
          ←
        </button>

        <button
          class="controls__arrow"
          @click="switchSlide('next')"
          :disabled="slideNumber === slides.length"
        >
          →
        </button>
      </section>

      <section class="slider__numbers">
        <span>{{ `0${slideNumber}` }}</span>

        <span>/</span>

        <span>{{ `0${slidesLength}` }}</span>
      </section>
    </section>
  </div>
</template>

<style lang="scss" scoped>
.slider {
  margin-top: 50px;

  @media (min-width: 768px) {
    display: flex;
  }

  &__numbers {
    display: flex;
    justify-content: center;
    margin-top: 10px;
    color: #bdbdbd;
    font-size: 18px;
    font-style: normal;
    font-weight: 400;
    line-height: 24px;
    gap: 20px;

    @media (min-width: 1024px) {
      font-size: 24px;
    }
  }

  .slide {
    position: relative;
    margin-top: 20px;

    &__view {
      display: block;
      position: absolute;
      bottom: 0;
      left: 0;
    }

    @media (min-width: 768px) {
      display: grid;
      margin-left: 50px;
      order: 1;
    }

    @media (min-width: 1024px) {
      margin-left: 100px;
    }

    @media (min-width: 1240px) {
      margin-left: 150px;
    }
  }

  .dummy {
    min-height: 289px;
  }
  .headline {
    display: flex;
    flex-direction: column;
    margin: auto;
    align-items: center;

    &__mobile {
      @media (min-width: 768px) {
        display: none;
      }
    }

    &__desktop {
      @media (min-width: 768px) {
        display: flex;
      }
    }

    @media (min-width: 768px) {
      margin-top: 100px;
      align-items: start;
      margin: 0;
    }

    @media (min-width: 1024px) {
      margin-top: 200px;
    }

    &__first-part {
      color: #bdbdbd;
      font-size: 64px;
      font-style: normal;
      font-weight: 300;
      line-height: 64px;
    }

    &__second-part {
      color: #333;
      font-size: 64px;
      font-style: normal;
      font-weight: 700;
      line-height: 64px;
    }
  }

  img {
    width: 100%;
  }

  .controls {
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin-top: 20px;
    gap: 20px;

    &__arrows {
      display: flex;
      justify-content: center;
      gap: 20px;
    }

    &__arrow {
      width: 35px;
      height: 35px;
      flex-shrink: 0;
      border: 1px solid #f2f2f2;
      background: #fff;
      transition: 0.3s;
      cursor: pointer;

      &:hover {
        background-color: #f2f2f2;
      }

      &:disabled {
        cursor: auto;
      }

      &:disabled:hover {
        background-color: white;
      }
    }

    @media (min-width: 768px) {
      align-items: baseline;
    }

    @media (min-width: 1240px) {
      gap: 80px;
    }
  }

  .v-enter-active,
  .v-leave-active {
    transition: opacity 0.5s ease;
  }

  .v-enter-from,
  .v-leave-to {
    opacity: 0;
  }
}
</style>
