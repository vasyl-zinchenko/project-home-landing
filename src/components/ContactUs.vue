<script setup>
import { computed, ref } from "vue";
import BaseButton from "./ui/BaseButton.vue";
import contactUs from "../assets/contact-us.jpg";

const name = ref("");
const tel = ref("");
const email = ref("");
const interest = ref("");
const message = ref("");
const isChecked = ref(false);

const isDisabled = computed(() => {
  return (
    !isChecked.value ||
    message.value.length === 0 ||
    email.value.length === 0 ||
    tel.value.length === 0
  );
});

const onSubmit = (event) => {
  event.preventDefault();
  name.value = "";
  tel.value = "";
  email.value = "";
  interest.value = "";
  message.value = "";
  isChecked.value = false;
};
</script>

<template>
  <div class="contact-us" id="contacts">
    <section class="contact-us__headline-wrapper">
      <h2>Contact us</h2>
    </section>

    <div class="contact-us__form-wrapper">
      <form class="contact-us__form" @submit="onSubmit">
        <input id="name" type="text" placeholder="Name" v-model="name" />

        <div class="required-input">
          <label for="phone" v-if="tel.length === 0">
            Phone number
            <span>*</span>
          </label>

          <input id="phone" type="tel" v-model="tel" />
        </div>

        <div class="required-input">
          <label for="email" v-if="email.length === 0">
            E-mail
            <span>*</span>
          </label>
          <input id="email" type="email" v-model="email" />
        </div>

        <input
          id="interest"
          type="text"
          v-model="interest"
          placeholder="Interested product/service"
        />

        <div class="required-input">
          <label for="message" v-if="message.length === 0">
            Message
            <span>*</span>
          </label>

          <textarea id="message" v-model="message" />
        </div>

        <div class="required-input__privacy">
          <input type="checkbox" v-model="isChecked" id="privacy" />

          <label class="privacy" for="privacy">
            By submitting an application you agree to the privacy policy
          </label>
        </div>

        <BaseButton
          :color="'white'"
          :backgroundColor="'#333'"
          :isDisabled="isDisabled"
        >
          send →
        </BaseButton>
      </form>

      <div
        class="contact-us__image"
        :style="{ backgroundImage: `url(${contactUs})` }"
      ></div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.contact-us {
  margin-top: 30px;
  &__form {
    display: flex;
    flex-direction: column;
    gap: 10px;

    &-wrapper {
      display: flex;
      flex-direction: column;
      gap: 30px;

      @media (min-width: 768px) {
        flex-direction: row;
      }

      @media (min-width: 1240px) {
        display: grid;
        grid-template-columns: 1.1fr 2fr;
      }
    }
  }

  &__headline-wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 10px;

    @media (min-width: 768px) {
      justify-content: start;
    }
  }

  &__image {
    height: 285px;
    width: 100%;
    background-size: 100% 100%;
    background-position: center;
    order: -1;

    @media (min-width: 768px) {
      order: 0;
    }
  }
}
input,
textarea,
.required-input {
  color: #8d8d8d;
  font-size: 14px;
  background: #f3f3f3;
  outline: none;
  border: none;

  &__privacy {
    display: flex;
    gap: 10px;
    background-color: white;
  }
}

input[type="text"] {
  padding: 10px 15px;
}

.privacy {
  color: #333;
  font-size: 14px;
  font-style: normal;
  font-weight: 400;
  letter-spacing: 0.42px;
  margin: 20px 0;
}

.required-input {
  position: relative;
  display: flex;
  padding: 10px 15px;

  & > input {
    display: flex;
  }

  & > label {
    display: flex;

    position: absolute;

    & > span {
      color: #c30000;
    }
  }
}

img {
  width: 100%;
}

.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

textarea {
  resize: none;
  width: 100%;
}
</style>
