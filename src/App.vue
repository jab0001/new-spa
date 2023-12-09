<template>
  <div
    class="layout"
    :style="isMenuOpen ? 'position: fixed; width: 100%; height: 100%' : ''"
  >
    <header class="layout__header header">
      <nav class="header__nav">
        <a href="">
          <img
            class="header__logo"
            src="./assets/img/logo-header.png"
            width="123"
            height="23"
            alt="logo qwqer-logo"
          />
        </a>
        <div class="header__container">
          <a class="header__link header__link-phone" href="tel:+88001234567"
            >8-800-123-45-67</a
          >
          <a class="header__link header__link-login" href="">Log in</a>
          <a class="header__link header__link-signup" href="">Sign up</a>
        </div>
        <button class="header__btn" @click="openMenu">
          <img class="header__icon" src="./assets/img/menu.svg" />
        </button>
      </nav>
    </header>
    <Menu v-if="isMenuOpen" @closeMenu="closeMenu" />
    <main class="layout__main">
      <Introduction @updateAddresses="updateAddresses" />
      <Service />
      <WeCare />
      <FirstOrder />
      <ShippingForm :items="items" @openModal="openModal" />
    </main>
    <footer class="layout__footer">
      <Footer />
      <div class="layout__footer-desktop">
        <ul class="layout__footer-list">
          <li class="layout__footer-item">
            <a class="layout__footer-link" href="" target="_blank"
              >Terms & Conditions</a
            >
          </li>
          <li class="layout__footer-item">
            <a class="layout__footer-link" href="" target="_blank"
              >Privacy Policy</a
            >
          </li>
          <li class="layout__footer-item">
            <a class="layout__footer-link" href="" target="_blank">FAQ</a>
          </li>
          <li class="layout__footer-item">2023</li>
        </ul>
      </div>
    </footer>
    <div class="fog" v-if="isOpenModal" @click="closeModal"></div>
    <Modal v-if="isOpenModal" @closeModal="closeModal" />
  </div>
</template>

<script>
import { Component, Vue } from "vue-property-decorator";
import Menu from "@/components/Menu.vue";
import Introduction from "@/components/Introduction.vue";
import Service from "@/components/Service.vue";
import WeCare from "@/components/WeCare.vue";
import FirstOrder from "@/components/FirstOrder.vue";
import ShippingForm from "@/components/ShippingForm.vue";
import Modal from "@/components/Modal.vue";
import Footer from "@/components/Footer.vue";

@Component({
  components: {
    Menu,
    Introduction,
    Service,
    WeCare,
    FirstOrder,
    ShippingForm,
    Modal,
    Footer,
  },
})
export default class Layout extends Vue {
  items = {};
  isOpenModal = false;
  isMenuOpen = false;

  updateAddresses(items) {
    this.items = items;
  }

  openModal() {
    this.isOpenModal = true;
  }

  closeModal() {
    this.isOpenModal = false;
  }

  closeMenu() {
    this.isMenuOpen = false;
  }

  openMenu() {
    this.isMenuOpen = true;
  }
}
</script>

<style lang="scss" scoped>
.fog {
  position: fixed;
  overflow: auto;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  backdrop-filter: blur(3px) brightness(0.5);
}

.layout {
  &__header {
    padding: 12px 16px;
  }

  &__main {
  }

  &__footer {
    min-height: 415px;
    background: #18191d;

    &-desktop {
      display: none;
    }
  }

  @media (min-width: 768px) {
    &__header {
      padding: 13px;
    }

    &__footer {
      min-height: inherit;
      &-desktop {
        display: block;
        border-top: 1px solid rgba(255, 255, 255, 0.15);
      }

      &-list {
        max-width: 1180px;
        margin: 0 auto;
        display: flex;
        padding: 20px 0;
      }

      &-item {
        font-family: "PollyRoundedThin", "Open Sans";
        font-size: 13px;
        font-weight: 300;
        line-height: 18px;
        text-align: left;

        color: rgba(255, 255, 255, 1);

        margin-left: 70px;

        &:first-child {
          margin: 0;
        }

        &:last-child {
          margin-left: auto;
        }
      }

      &-link {
        text-decoration: none;
        color: rgba(255, 255, 255, 1);
      }
    }
  }
}

.header {
  &__nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  &__btn {
    padding: 0;
    border: none;
    background: none;
  }

  &__icon {
    padding: 4px;
  }

  &__container {
    display: none;
  }

  @media (min-width: 768px) {
    max-width: 1180px;
    margin: 0 auto;
    &__logo {
      width: 157px;
      height: 29px;
    }

    &__btn {
      display: none;
    }

    &__container {
      display: flex;
    }

    &__link {
      display: flex;
      align-items: center;
      text-align: left;

      text-decoration: none;

      color: #18191d;

      &-phone {
        margin-right: 101px;
        font-family: "PollyRoundedThin", "Open Sans";
        font-size: 18px;
        font-weight: 300;
        line-height: 22px;

        color: #18191d;
      }

      &-login {
        margin-right: 44px;
        font-family: "PollyRoundedRegular", "Open Sans";
        font-size: 18px;
        font-weight: 400;
        line-height: 22px;
        text-align: left;

        color: #18191d;
      }

      &-signup {
        padding: 12px 24px;
        background: #112e95;
        border-radius: 30px;

        font-family: "PollyRoundedRegular", "Open Sans";
        font-size: 18px;
        font-weight: 400;
        line-height: 22px;
        text-align: left;

        color: #fff;

        &:active {
          opacity: 1;
          background: #0c247d;
        }
      }
    }
  }
}
</style>
