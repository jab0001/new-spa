<template>
  <div class="introduction">
    <div class="introduction__wrapper">
      <div style="width: fit-content; position: relative; left: -14px">
        <img class="introduction__img" src="../assets/img/boxes.png" />
        <div class="introduction__rule">
          <p class="introduction__rule-text">Set the delivery price yourself</p>
        </div>
      </div>
    </div>
    <div class="introduction__wrapper-desktop">
      <div class="introduction__container-desktop">
        <div class="introduction__container">
          <h2 class="introduction__title">
            Same-day courier delivery from 15 minutes
            <span>in Los-Angeles</span>
          </h2>
          <p class="introduction__inform">
            <span>QWQ5 - </span>Promo code: $5 first delivery discount
          </p>
          <p class="introduction__description">
            Express courier delivery service within the city. Flowers, gifts,
            and any other goods. We fulfill all your wishes
          </p>
        </div>

        <div class="introduction__form">
          <AddressInput
            v-for="(input, index) in inputs"
            :key="index"
            :item="input"
            :section="`introduction`"
          />
          <button class="introduction__btn" @click="buttonHandler">
            Calculate the cost
          </button>
        </div>
      </div>

      <div class="introduction__desktop">
        <img class="introduction__img" src="../assets/img/boxes-desktop.png" />
        <div class="introduction__rule">
          <p class="introduction__rule-text">Set the delivery price yourself</p>
        </div>
      </div>
    </div>
    <img
      class="introduction__line introduction__line-one"
      src="../assets/img/lines/line-introduction-1.svg"
    />
    <img
      class="introduction__line introduction__line-two"
      src="../assets/img/lines/line-introduction-2.svg"
    />
  </div>
</template>

<script>
import { Component, Vue } from "vue-property-decorator";
import AddressInput from "@/components/Inputs/AddressInput.vue";

@Component({
  components: {
    AddressInput,
  },
})
export default class Introduction extends Vue {
  inputs = {
    sender: {
      value: "",
      placeholder: "Sender address",
      name: "sender",
      img: true,
    },
    recepient: {
      value: "",
      placeholder: "Recipient address",
      name: "recepient",
      img: true,
    },
  };

  buttonHandler() {
    const element = document.querySelector("#calculator");
    let top = element.offsetTop;

    window.scrollTo(0, top);

    this.$emit("updateAddresses", {
      sender: this.inputs.sender.value,
      recipient: this.inputs.recepient.value,
    });
  }
}
</script>

<style lang="scss" scoped>
.introduction {
  background: #fbfbfb;
  padding-bottom: 40px;

  background-image: url("@/assets/img/mobile-line-introduction.svg");
  background-repeat: no-repeat;
  background-size: 100%;
  background-position: 0px 80px;

  &__line {
    display: none;
  }

  &__desktop {
    display: none;
  }

  &__wrapper {
    display: flex;
    justify-content: center;
    padding-top: 28px;
  }

  &__container {
    padding: 0px 16px;
  }

  &__img {
    width: 201px;
    height: 216px;
  }

  &__rule {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 80px;
    height: 80px;
    border-radius: 50%;
    background-color: #37352f;
    position: absolute;
    top: -8px;
    right: -36px;

    &-text {
      font-family: "PollyRoundedRegular", "Open Sans";
      font-size: 9px;
      font-weight: 400;
      line-height: 12px;
      text-align: center;
      max-width: 68px;

      color: #fff;
    }
  }

  &__title {
    padding-top: 11px;

    font-family: "PollyRoundedRegular", "Open Sans";
    font-size: 40px;
    font-weight: 400;
    line-height: 42px;
    text-align: left;

    color: #18191d;

    span {
      color: #112e95;
    }
  }

  &__inform {
    padding-top: 25px;
    font-family: "PollyRoundedRegular", "Open Sans";
    font-size: 15px;
    font-weight: 400;
    line-height: 22px;
    text-align: left;

    color: #18191d;

    span {
      color: #112e95;
    }
  }

  &__description {
    padding-top: 16px;
    font-family: "PollyRoundedThin", "Open Sans";
    font-size: 15px;
    font-weight: 300;
    line-height: 22px;
    letter-spacing: 0.1px;
    text-align: left;
  }

  &__form {
    margin: 24px 16px 0 16px;
    padding: 16px;
    display: flex;
    flex-direction: column;
    min-height: 212px;
    border-radius: 16px;

    box-shadow: 0px 12px 28px 5px rgba(15, 15, 15, 0.15);
  }

  &__btn {
    margin-top: auto;
    padding: 19px 68px;

    font-family: "PollyRoundedRegular", "Open Sans";
    font-size: 18px;
    font-weight: 400;
    line-height: 22px;
    text-align: center;

    border: none;
    border-radius: 30px;
    background: #112e95;

    color: #fff;

    cursor: pointer;

    &:hover {
      background: #445eb8;
    }

    &:active {
      opacity: 1;
      background: #0c247d;
    }
  }

  @media (min-width: 768px) {
    padding-bottom: 88px;
    padding-left: 13px;
    padding-right: 13px;
    background-image: initial;
    position: relative;

    &__wrapper {
      display: none;
    }

    &__container {
      padding: 0;

      &-desktop {
        max-width: 680px;
        z-index: 10;
      }
    }

    &__title {
      padding-top: 65px;
      max-width: 680px;
      line-height: 48px;
    }

    &__inform {
      padding-top: 39px;
      font-size: 18px;
    }

    &__description {
      max-width: 580px;
      font-size: 18px;
    }

    &__wrapper-desktop {
      max-width: 1180px;
      margin: 0 auto;
      position: relative;
      z-index: 2;

      display: flex;
    }

    &__form {
      margin: 0;
      padding: 40px;
      margin-top: 59px;
      max-width: 580px;
      box-sizing: border-box;
      background: #fff;
    }

    &__desktop {
      display: block;
      position: absolute;
      bottom: -67px;
      right: -136px;
    }

    &__img {
      width: 690px;
      height: auto;
    }

    &__rule {
      width: 116px;
      height: 116px;
      top: -26px;
      right: 167px;

      &-text {
        font-size: 14px;
        font-weight: 400;
        line-height: 18px;

        max-width: initial;
      }
    }

    &__btn {
      margin-top: 32px;
    }

    &__line {
      display: block;
      position: absolute;
      z-index: 1;

      &-one {
        bottom: 0;
        width: 25vw;
        height: auto;
      }

      &-two {
        top: 0;
        right: 0;
        width: 49vw;
        height: auto;
      }
    }
  }

  @media (min-width: 768px) and (max-width: 1400px) {
    &__line {
      &-one {
        bottom: 0;
        width: 25vw;
        height: auto;
      }

      &-two {
        top: 28%;
        right: 0;
        width: 49vw;
        height: auto;
      }
    }
  }
}
</style>
