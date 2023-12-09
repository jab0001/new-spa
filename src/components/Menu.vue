<template>
  <div class="menu">
    <div class="menu__nav">
      <a href="">
        <img
          class="menu__logo"
          src="../assets/img/logo-header-menu.png"
          width="137"
          height="25"
          alt="logo qwqer-logo"
        />
      </a>
      <svg
        @click="closeMenu"
        width="24"
        height="25"
        viewBox="0 0 24 25"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M20 20.5479L4 4.54785M20 4.54785L4 20.5479"
          stroke="white"
          stroke-width="1.88"
          stroke-linecap="round"
        />
      </svg>
    </div>
    <div class="menu__content">
      <a class="menu__link menu__link-phone" href="tel:+8334679737"
        >(833) 467-9737</a
      >
      <ul class="menu__list menu__list-sections">
        <li
          class="menu__item menu__item-sections"
          v-for="menu in menuItems"
          :key="menu.text"
        >
          <a
            class="menu__link menu__link-sections"
            :href="menu.url"
            @click="closeMenu"
            >{{ menu.text }}</a
          >
        </li>
      </ul>
    </div>
    <ul class="menu__list menu__list-enter">
      <li
        class="menu__item menu__item-enter"
        v-for="enter in enterItems"
        :key="enter.text"
      >
        <a
          :class="`menu__link menu__link-enter menu__link-enter-${enter.class}`"
          :href="enter.url"
          target="_blank"
        >
          {{ enter.text }}</a
        >
      </li>
    </ul>
  </div>
</template>

<script>
import { Component, Vue } from "vue-property-decorator";

@Component({})
export default class Menu extends Vue {
  menuItems = [
    {
      text: "what are we carrying?",
      url: "#carrying",
    },
    {
      text: "Stages",
      url: "#stages",
    },
    {
      text: "Calculate ",
      url: "#calculator",
    },
  ];

  enterItems = [
    {
      text: "Log in",
      url: "#",
      class: "login",
    },
    {
      text: "Sign up",
      url: "#",
      class: "signin",
    },
  ];
  closeMenu() {
    this.$emit("closeMenu");
  }
}
</script>

<style lang="scss" scoped>
.menu {
  position: fixed;
  display: flex;
  flex-direction: column;
  align-items: center;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  background: #112e95;
  box-sizing: border-box;
  z-index: 500;

  &__nav {
    display: flex;
    justify-content: space-between;
    width: 100%;
    padding: 14px 18px 14px 16px;
    box-sizing: border-box;
  }

  &__content {
    margin-top: 50px;
    padding: 0 5vw;
  }

  &__list {
    &-sections {
      margin-top: 80px;
    }

    &-enter {
      min-width: 250px;
      margin-top: auto;
      margin-bottom: 48px;
      display: flex;
      justify-content: space-between;
    }
  }

  &__item {
    &-sections {
      &:not(:first-child) {
        margin-top: 28px;
      }
    }
  }

  &__link {
    text-decoration: none;
    color: #fff;

    font-family: "PollyRoundedRegular", "Open Sans";
    text-align: left;

    &-phone {
      font-family: "PollyRoundedThin", "Open Sans";
      font-size: 20px;
      font-weight: 300;
      line-height: 24px;
    }

    &-sections {
      font-size: 28px;
      font-weight: 400;
      line-height: 32px;
    }

    &-enter {
      font-size: 18px;
      font-weight: 400;
      line-height: 22px;

      &-signin {
        padding: 12px 24px;
        background: #27aaa8;
        border-radius: 30px;
      }
    }
  }
}
</style>
