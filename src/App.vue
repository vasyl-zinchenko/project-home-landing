<script setup>
import Header from "./components/layouts/TheHeader.vue";
import Slider from "./components/TheSlider.vue";
import AboutCompany from "./components/AboutCompany.vue";
import MainTasks from "./components/MainTasks.vue";
import OurProjects from "./components/OurProjects.vue";
import ContactUs from "./components/ContactUs.vue";
import Footer from "./components/layouts/TheFooter.vue";
</script>

<template>
  <div class="container">
    <Header />
    <Slider />
    <AboutCompany />
    <MainTasks />
    <OurProjects />
    <ContactUs />
  </div>
  <Footer />
</template>

<style scoped lang="scss">
.container {
  padding: 10px 20px;
  max-width: 1170px;
	margin: auto;

  @media (min-width: 1024px) {
    padding: 20px 40px;
  }
}
</style>
