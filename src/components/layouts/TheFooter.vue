<script setup>
import logo from "../../assets/logo-footer.svg";
import facebook from "../../assets/social/facebook.svg";
import linkedin from "../../assets/social/linkedin.svg";
import pinterest from "../../assets/social/pinterest.svg";
import twitter from "../../assets/social/twitter.svg";
import adress from "../../assets/contact/adress.svg";
import tel from "../../assets/contact/tel.svg";
import email from "../../assets/contact/email.svg";

const listItem = [
  { id: 1, title: "Home", href: "#" },
  { id: 2, title: "Galery", href: "#galery" },
  { id: 3, title: "Projects", href: "#projects" },
  { id: 4, title: "Certificates", href: "#certificates" },
  { id: 5, title: "Contacts", href: "#contacts" },
];

const socialMedia = [
  { id: 1, src: facebook, alt: "facebook", href: "#" },
  { id: 2, src: twitter, alt: "twitter", href: "#" },
  { id: 3, src: linkedin, alt: "linkedin", href: "#" },
  { id: 4, src: pinterest, alt: "pinterest", href: "#" },
];
</script>

<template>
  <section class="footer">
    <div class="footer__main">
      <img class="logo" :src="logo" alt="Logo" />

      <section class="footer__information">
        <ul class="footer__information__list">
          <p class="footer__title">Information</p>

          <li
            class="footer__information__list-item"
            v-for="item in listItem"
            :key="item.id"
          >
            <a :href="item.href">{{ item.title }}</a>
          </li>
        </ul>
      </section>

      <section class="footer__contacts">
        <p class="footer__title">Contacts</p>

        <div class="footer__contacts_wrapper">
          <div>
            <img :src="adress" alt="adress" />
            <span
              >100000, The Republic of Kazakhstan, Karaganda, Televiziina St
              10</span
            >
          </div>

          <div>
            <img :src="tel" alt="tel" />
            <span><a href="tel:+380000000000">+38 (000) 000 00 00</a></span>
          </div>

          <div>
            <img :src="email" alt="email" />
            <span><a href="mailto:mail@gmail.com">mail@gmail.com</a></span>
          </div>
        </div>
      </section>

      <section class="footer__social">
        <p class="footer__title">Social media</p>

        <div class="footer__social_icons">
          <a v-for="item in socialMedia" :key="item.id" :href="item.href">
            <img
              :class="`footer__social_icons-${item.alt}`"
              :src="item.src"
              :alt="item.alt"
            />
          </a>
        </div>
      </section>
    </div>

    <div class="underline"></div>

    <section class="copyright">
      <p>© 2019 Digital Project. All rights reserved.</p>
    </section>
  </section>
</template>

<style lang="scss" scoped>
.footer {
  margin-top: 120px;
  background: #2c2c2c;
  color: white;

  &__main {
    padding: 10px 20px;
    margin-bottom: 60px;
    max-width: 1170px;
    margin: auto;

    @media (min-width: 768px) {
      align-items: start;
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
    }

    @media (min-width: 1024px) {
      padding: 20px 40px;
    }

    @media (min-width: 1240px) {
      padding: 20px 40px;
    }
  }

  &__title {
    font-size: 16px;
    font-weight: 700;
    margin-top: 30px;
    margin-bottom: 25px;
    text-decoration: underline;

    @media (min-width: 768px) {
      text-decoration: none;
    }
  }

  &__information {
    &__list {
      &-item {
        @media (min-width: 1024px) {
          margin-bottom: 12px;
        }
      }
    }
  }

  &__contacts {
    max-width: 300px;

    @media (min-width: 768px) {
      max-width: 250px;
    }
    &_wrapper {
      display: flex;
      flex-direction: column;
      gap: 20px;

      @media (min-width: 1024px) {
        gap: 30px;
      }

      & > div {
        display: flex;
        align-items: center;
        gap: 19px;
      }
    }
  }

  &__social {
    &_icons {
      display: flex;
      gap: 40px;

      @media (min-width: 768px) {
        gap: 20px;
      }

      @media (min-width: 1240px) {
        gap: 40px;
      }

      &-facebook:hover {
        filter: invert(47%) sepia(84%) saturate(2916%) hue-rotate(171deg)
          brightness(87%) contrast(93%);
      }
      &-twitter:hover {
        filter: invert(47%) sepia(84%) saturate(2916%) hue-rotate(164deg)
          brightness(92%) contrast(93%);
      }
      &-linkedin {
        position: relative;
        &:hover {
          filter: invert(46%) sepia(84%) saturate(2916%) hue-rotate(176deg)
            brightness(78%) contrast(93%);
        }
      }
      &-pinterest:hover {
        filter: invert(47%) sepia(84%) saturate(2916%) hue-rotate(-39deg)
          brightness(105%) contrast(93%);
      }
    }
  }
}

li,
span {
  font-size: 14px;
  font-weight: 500;
  line-height: 24px;
  letter-spacing: 0.42px;
}

.underline {
  height: 1px;
  background-color: #fff;
  opacity: 0.1;
}

.copyright {
  display: flex;
  justify-content: center;
  color: rgba(200, 200, 200, 0.5);
  font-size: 12px;
  font-weight: 400;
  line-height: 22px;
  padding: 25px 0;
}

.logo {
  margin-top: 30px;

  @media (min-width: 768px) {
    width: 100px;
    width: 145px;
  }
}

a {
  color: white;

  &:hover {
    text-decoration: underline;
  }
}
</style>
