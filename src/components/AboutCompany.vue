<script setup>
import AboutCompany1 from "../assets/about/about-company-01.jpg";
import AboutCompany2 from "../assets/about/about-company-02.jpg";
import AboutCompany3 from "../assets/about/about-company-03.jpg";
import BaseButton from "./ui/BaseButton.vue";
</script>

<template>
  <section class="about-company" id="certificates">
    <h2 class="mobile-headline">About the company</h2>

    <section class="about-company__images">
      <div class="about-company__images-first">
        <img :src="AboutCompany1" alt="AboutCompany1" />

        <img :src="AboutCompany2" alt="AboutCompany2" />
      </div>

      <div>
        <img :src="AboutCompany3" alt="AboutCompany3" />
      </div>
    </section>

    <section class="about-company__content">
      <h2 class="about-company__content-headline">About the company</h2>

      <p>
        Lorem Ipsum is simply dummy text of the printing and typesetting
        industry. Lorem Ipsum has been the industry's standard dummy text ever
        since the 1500s, when an unknown printer took a galley of type and
        scrambled it to make a type specimen book. It has survived not only five
        centuries.
      </p>

      <BaseButton :color="'#333'" :backgroundColor="'white'">
        Read →
      </BaseButton>
    </section>
  </section>
</template>

<style lang="scss" scoped>
.about-company {
  position: relative;
  margin-top: 30px;

  &::after {
    background-color: #fbfbfb;
    content: "";
    position: absolute;
    height: -webkit-fill-available;
    width: 100%;
    z-index: -1;

    @media (min-width: 768px) {
      width: -webkit-fill-available;
    }

    @media (min-width: 1024px) {
      height: 425px;
    }
  }

  &__images {
    display: grid;
    gap: 10px;
    grid-template-columns: 1fr 1fr;
    padding: 10px;
    place-items: center;

    @media (min-width: 1024px) {
      padding: 30px 0 0 40px;
      gap: 20px;
    }

    @media (min-width: 1240px) {
      padding: 30px 0 0 100px;
      gap: 30px;
    }

    &-first {
      @media (min-width: 1024px) {
        display: flex;
        flex-direction: column;
        gap: 20px;
      }

      @media (min-width: 1240px) {
        gap: 30px;
      }
    }
  }

  &__content {
    margin-top: 10px;
    & > p {
      color: #000;
      font-size: 13px;
      font-weight: 300;
      padding: 10px;

      @media (min-width: 1024px) {
        font-size: 16px;
        line-height: 25px;
      }
    }

    &-headline {
      display: none;
      @media (min-width: 768px) {
        display: block;
      }

      @media (min-width: 1240px) {
        margin-top: 15px;
      }
    }

    @media (min-width: 768px) {
      display: flex;
      flex-direction: column;
      max-width: 300px;
    }

    @media (min-width: 1024px) {
      max-width: 400px;
      margin-left: 30px;
      padding-right: 30px;
    }
  }

  @media (min-width: 768px) {
    display: flex;
  }

  @media (min-width: 1240px) {
    display: grid;
    grid-template-columns: 1.2fr 1fr;
    margin-top: 120px;
  }
}

img {
  width: 100%;
}

button {
  margin-top: 10px;
}

.mobile-headline {
  @media (min-width: 768px) {
    display: none;
  }
}
</style>
