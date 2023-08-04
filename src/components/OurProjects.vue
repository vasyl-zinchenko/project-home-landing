<script setup>
import { computed, onMounted, ref, watch } from "vue";
import project1 from "../assets/projects/project-1.jpg";
import project2 from "../assets/projects/project-2.jpg";
import project3 from "../assets/projects/project-3.jpg";
import project4 from "../assets/projects/project-4.jpg";
import project5 from "../assets/projects/project-5.jpg";
import { useElementSize } from "@vueuse/core";
import BaseButton from "./ui/BaseButton.vue";

const projects = ref([
  { id: 1, title: "RECREATION CENTER", image: project1, isHovered: false },
  { id: 2, title: "Project", image: project2, isHovered: false },
  { id: 3, title: "Project", image: project3, isHovered: false },
  { id: 4, title: "Project", image: project4, isHovered: false },
  { id: 5, title: "Project", image: project5, isHovered: false },
]);

const el = ref(null);
const { width, height } = useElementSize(el);

const imageHeigth = ref(125);

watch(width, (newWidth, oldWidth) => {
  imageHeigth.value = width.value / 2;

  if (newWidth > oldWidth) {
    imageHeigth.value += 2;
  } else if (newWidth < oldWidth) {
    imageHeigth.value -= 2;
  }
  if (imageHeigth.value >= 255) {
    imageHeigth.value = 255;
  }
});
</script>

<template>
  <div class="projects" id="projects">
    <h2>Our projects</h2>

    <section ref="el" class="projects__images">
      <div
        class="project"
        v-for="project in projects"
        :key="project.id"
        :class="`project__images--${project.id} image`"
        :style="{
          backgroundImage: `url(${project.image})`,
          height: imageHeigth + 'px',
        }"
        @mouseover="project.isHovered = true"
        @mouseleave="project.isHovered = false"
      >
        <Transition>
          <div :class="{ hidden: !project.isHovered }">
            <span>{{ project.title }}</span>

            <a href="#">More details →</a>
          </div>
        </Transition>
      </div>
    </section>

    <div class="projects__all-projects">
      <BaseButton :color="'white'" :backgroundColor="'#333'">
        All projects →
      </BaseButton>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.projects {
  margin-top: 30px;
  &__images {
    display: grid;
    gap: 20px;
    grid-template-areas:
      "first first"
      "second second"
      "fourth fourth"
      "third fifth";

    @media (min-width: 768px) {
      grid-template-areas:
        "first first first first first second second second second second"
        "third third fourth fourth fourth fourth fourth fifth fifth fifth";
      grid-template-columns: repeat(10, 1fr);
    }

    @media (min-width: 1024px) {
      gap: 30px;
    }
  }

  &__all-projects {
    display: flex;
    justify-content: end;
    margin-top: 30px;
  }
  @media (min-width: 1024px) {
    margin-top: 120px;
  }
}

.project {
  position: relative;
  display: flex;
  justify-content: start;
  align-items: center;
  box-sizing: border-box;

  &::before {
    content: "";
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background: rgba(0, 0, 0, 0);
    transition: 0.3s;
  }

  &:hover:before {
    background: rgba(0, 0, 0, 0.79);
  }

  & > div {
    display: flex;
    flex-direction: column;
    gap: 10px;
    padding: 0 20px;
    max-width: 250px;
    z-index: 1;

    & > span {
      color: #fff;
      font-size: 20px;
      font-style: normal;
      font-weight: 700;
      text-transform: uppercase;

      @media (min-width: 1024px) {
        font-size: 26px;
      }

      @media (min-width: 1240px) {
        font-size: 43px;
        line-height: 64px;
      }
    }

    & > button {
      display: flex;
      background: none;
      color: white;
      text-transform: uppercase;
      font-size: 12px;
    }
  }
  &__images {
    &--1 {
      grid-area: first;
    }
    &--2 {
      grid-area: second;
    }
    &--3 {
      grid-area: third;
    }
    &--4 {
      grid-area: fourth;
    }
    &--5 {
      grid-area: fifth;
    }
  }
}

a {
  color: white;

  &:hover {
    cursor: pointer;
    text-decoration: underline;
  }
}

.image {
  background-size: 100% 100%;
  background-position: center;
  display: flex;
  justify-content: center;
}

.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

.hidden {
  visibility: hidden;
}

h2 {
  display: flex;
  justify-content: center;

  @media (min-width: 1024px) {
    margin-bottom: 60px;
    justify-content: start;
  }
}
</style>
