<script setup>
import { ref } from "vue";

const tasks = ref([
  {
    id: 1,
    number: 1,
    text: "Creating comfortable conditions and improving the quality of customer service",
  },
  {
    id: 2,
    number: 2,
    text: "Constantly improve the quality of services through staff training, purchase of new equipment and increased advertising in the market",
  },
]);
</script>

<template>
  <section class="tasks">
    <h2>Main tasks</h2>

    <div class="tasks__wrapper">
      <div class="task" v-for="task in tasks" :key="task.id">
        <span>{{ task.number }}</span>

        <p>{{ task.text }}</p>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.tasks {
  margin-top: 40px;

  gap: 20px;

  @media (min-width: 1024px) {
    margin-top: 120px;
  }

  &__wrapper {
    display: flex;
    flex-direction: column;
    @media (min-width: 1024px) {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 100px;
    }
  }
}
.task {
  display: flex;
  align-items: center;
  margin: auto;
  max-width: 400px;
  gap: 25px;

  & > span {
    color: #f2f2f2;
    font-size: 100px;
    font-weight: 900;

    @media (min-width: 1024px) {
      font-size: 180px;
      line-height: 0.9;
    }

    @media (min-width: 1240px) {
      font-size: 200px;
    }
  }

  & > p {
    color: #333;
    font-size: 17px;
    font-weight: 400;

    @media (min-width: 1024px) {
      font-size: 18px;
      line-height: 36px;
    }

    @media (min-width: 1240px) {
      font-size: 22px;
    }
  }

  &:first-child {
    @media (min-width: 1024px) {
      max-width: 300px;
    }

    @media (min-width: 1240px) {
      max-width: 350px;
    }
  }

  &:last-child {
    @media (min-width: 1024px) {
      max-width: 500px;
    }
  }

  @media (min-width: 1024px) {
    margin: 0;
    max-width: 100%;
    align-items: start;
  }
  @media (min-width: 1240px) {
    max-width: 100%;
  }
}

h2 {
  display: flex;
  justify-content: center;

  @media (min-width: 1024px) {
    justify-content: start;
  }
}
</style>
