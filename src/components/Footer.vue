<template>
  <div class="footer">
    <a href="">
      <img
        class="footer__logo"
        src="../assets/img/logo-footer.png"
        width="164"
        height="31"
        alt="logo qwqer-logo"
      />
    </a>
    <ul class="footer__list footer__list-menu">
      <li
        class="footer__item footer__item-menu"
        v-for="item in menuItems"
        :key="item.text"
      >
        <a class="footer__link footer__link-menu" :href="item.url">
          {{ item.text }}</a
        >
      </li>
    </ul>
    <div class="footer__wrapper">
      <a class="footer__link footer__link-mail" href="mailto:help@qwqer.com"
        >help@qwqer.com</a
      ><a class="footer__link footer__link-phone" href="tel:+8334679737"
        >(833) 467-9737</a
      >
    </div>
    <ul class="footer__list footer__list-social">
      <li
        class="footer__item footer__item-social"
        v-for="social in socialItems"
        :key="social.img"
      >
        <a class="footer__link footer__link-social" :href="social.url">
          <img
            :class="`footer__img-social footer__img-social-${social.img}`"
            :src="`../img/logo-${social.img}.png`"
          />
        </a>
      </li>
    </ul>
    <ul class="footer__list footer__list-app">
      <li
        class="footer__item footer__item-app"
        v-for="app in appItems"
        :key="app.img"
      >
        <a class="footer__link footer__link-app" :href="app.url">
          <img
            :class="`footer__img-app footer__img-app-${app.img}`"
            :src="`../img/app-${app.img}.png`"
          />
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
import { Component, Vue } from "vue-property-decorator";

@Component({})
export default class Footer extends Vue {
  menuItems = [
    {
      text: "What are we carrying?",
      url: "#carrying",
    },
    {
      text: "Stages",
      url: "#stages",
    },
    {
      text: "Calculate",
      url: "#calculator",
    },
  ];
  socialItems = [
    {
      img: "instagram",
      url: "",
    },
    {
      img: "linkedin",
      url: "",
    },
    {
      img: "facebook",
      url: "",
    },
  ];

  appItems = [
    {
      img: "apple",
      url: "",
    },
    {
      img: "google",
      url: "",
    },
  ];
}
</script>

<style lang="scss" scoped>
.footer {
  padding: 28px 20px 20px 16px;
  color: #fff;
  margin: 0 auto;
  max-width: 375px;

  &__logo {
  }

  &__wrapper {
    margin-top: 40px;
    display: flex;
    flex-direction: column;
  }

  &__list {
    display: flex;
    flex-direction: column;

    &-menu {
      margin-top: 35px;
    }

    &-social {
      margin-top: 19px;
      flex-direction: row;
      width: 43%;
      justify-content: space-between;
    }

    &-app {
      margin-top: 31px;
      flex-direction: row;
      justify-content: space-between;
    }
  }

  &__item {
    &-menu {
      &:not(:first-child) {
        margin-top: 12px;
      }
    }

    &-social {
    }
  }

  &__link {
    text-decoration: none;

    font-family: "PollyRoundedThin", "Open Sans";
    font-size: 14px;
    font-weight: 300;
    line-height: 20px;
    text-align: left;
    color: #fff;
    &-menu {
    }

    &-phone {
      margin-top: 12px;
    }

    &-mail {
      font-family: "PollyRoundedRegular", "Open Sans";
      font-size: 24px;
      font-weight: 400;
      line-height: 28px;
    }

    &-social {
      display: flex;
    }
  }

  &__img {
    &-social {
      &-instagram {
        width: 20px;
        height: 20px;
      }

      &-linkedin {
        width: 22px;
        height: 22px;
      }

      &-facebook {
        width: 21px;
        height: 20px;
      }
    }

    &-app {
      width: 153px;
      height: 40px;
      &-google {
      }

      &-apple {
      }
    }
  }

  @media (min-width: 768px) {
    display: flex;
    max-width: 1180px;
    margin: 0 auto;
    padding-top: 74px;
    flex-wrap: wrap;

    &__logo {
      width: 186px;
      height: 35px;
    }

    &__item {
      &-menu {
        &:not(:first-child) {
          margin-top: 0;
        }
      }

      &-app {
        &:last-child {
          margin-left: 12px;
        }
      }
    }

    &__list {
      &-social {
        order: 2;
        margin-left: auto;
        margin-top: 63px;
        width: 142px;
      }

      &-app {
        order: 1;
        margin-top: 50px;
      }

      &-menu {
        margin: 0;
        max-height: 58px;
        min-width: 409px;
        display: flex;
        flex-direction: column;
        flex-wrap: wrap;
        justify-content: space-between;
        margin-left: auto;
      }
    }

    &__wrapper {
      margin: 0;
      margin-left: 125px;
    }

    &__link {
      font-size: 16px;
      line-height: 24px;

      &-mail {
        font-size: 28px;
        line-height: 32px;
      }

      &-phone {
        font-size: 16px;
        line-height: 24px;
        text-align: right;
        margin-top: 3px;
      }
    }

    &__img {
      &-app {
        width: 138px;
        height: 40px;
      }
    }
  }

  @media (min-width: 768px) and (max-width: 1000px) {
    &__wrapper {
      margin-top: 20px;
      margin-left: 0;
      width: 100%;
    }

    &__link {
      &-mail {
        text-align: right;
      }
    }
  }
}
</style>
