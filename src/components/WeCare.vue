<template>
  <div class="care" id="stages">
    <h2 class="care__title">We take care of your orders at every stage</h2>
    <ul class="care__list">
      <li class="care__item" v-for="card in cards" :key="card.id">
        <div class="care__circle">
          <div class="care__circle-first">
            <div class="care__circle-second">
              <p class="care__circle-number">{{ card.id }}</p>
            </div>
          </div>
        </div>
        <h3 class="care__title-item">{{ card.title }}</h3>
        <p class="care__description">{{ card.description }}</p>
      </li>
    </ul>
    <img
      class="care__line care__line-one"
      src="../assets/img/lines/line-care-1.svg"
    />
    <img
      class="care__line care__line-two"
      src="../assets/img/lines/line-care-between-1.svg"
    />
    <img
      class="care__line care__line-three"
      src="../assets/img/lines/line-care-2.svg"
    />
    <img
      class="care__line care__line-four"
      src="../assets/img/lines/line-care-between-2.svg"
    />
  </div>
</template>

<script>
import { Component, Vue } from "vue-property-decorator";

@Component({})
export default class WeCare extends Vue {
  cards = [
    {
      id: 1,
      img: "",
      title: "Simple Order",
      description:
        "Ordering a delivery is easy and convenient, a user-friendly website, and the app.",
    },
    {
      id: 2,
      img: "",
      title: "Reliable Delivery",
      description:
        "We guarantee fast and high-quality delivery, ensuring packages arrive to recipients on time and in the best condition.",
    },
    {
      id: 3,
      img: "",
      title: "Trusted Couriers",
      description:
        "All couriers undergo a special training, and our support service is always available and ready to assist.",
    },
  ];
}
</script>

<style lang="scss" scoped>
.care {
  background-image: url("@/assets/img/weCare-background.svg");
  background-repeat: no-repeat;
  background-size: 111%;
  background-position: -38px 135px;
  margin-bottom: 40px;

  &__line {
    display: none;
  }

  &__title {
    margin-top: 40px;

    font-family: "PollyRoundedRegular", "Open Sans";
    font-size: 36px;
    font-weight: 400;
    line-height: 38px;
    text-align: center;

    color: #18191d;

    &-item {
      margin-top: 32px;

      font-family: "PollyRoundedRegular", "Open Sans";
      font-size: 24px;
      font-weight: 400;
      line-height: 28px;
      text-align: center;

      color: #18191d;
    }
  }

  &__list {
    margin-top: 32px;
  }

  &__item {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    padding-bottom: 20px;
    padding-top: 20px;

    &:not(:first-child) {
      margin-top: 40px;
    }
  }

  &__circle {
    width: 100%;
    display: flex;
    justify-content: center;

    &-first {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 178px;
      height: 178px;
      border-radius: 50%;
      background: #bce5e4;
    }

    &-second {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 127px;
      height: 127px;
      border-radius: 50%;
      background: #20a7a5;
    }

    &-number {
      font-family: "PollyRoundedRegular", "Open Sans";
      font-size: 60px;
      font-weight: 700;
      line-height: 72px;
      position: relative;
      top: -4px;

      color: #fff;
    }
  }

  &__description {
    margin-top: 20px;

    font-family: "PollyRoundedThin", "Open Sans";
    font-size: 16px;
    font-weight: 300;
    line-height: 22px;
    text-align: center;
    width: 90%;
  }

  @media (min-width: 768px) {
    margin-bottom: 90px;
    background-image: initial;
    position: relative;

    &__title {
      margin: 0 auto;
      margin-top: 92px;
      max-width: 876px;

      font-size: 64px;
      line-height: 68px;

      &-item {
        font-size: 28px;
        line-height: 32px;
        margin-top: 40px;
      }
    }

    &__description {
      margin-top: 21px;
      font-size: 18px;
      line-height: 24px;

      width: 100%;
    }

    &__list {
      margin: 0 auto;
      margin-top: 80px;
      display: flex;
      max-width: 1137px;

      justify-content: space-between;
    }

    &__item {
      max-width: 343px;
      min-height: 401px;
      display: block;
      padding: 0;

      &:not(:first-child) {
        margin: 0;
      }
    }

    &__circle {
      z-index: 1;
      position: relative;
      &-first {
        width: 209px;
        height: 209px;
      }

      &-second {
        width: 155px;
        height: 155px;
      }

      &-number {
        font-size: 80px;
        line-height: 96px;
      }
    }

    &__line {
      display: block;
      position: absolute;

      &-one {
        bottom: -2vw;
        left: 0;
        width: 24vw;
        height: auto;
      }

      &-two {
        bottom: 13.5vw;
        left: 34vw;
        width: 11vw;
        height: auto;
      }

      &-three {
        top: -5.5vw;
        right: 8vw;
        width: 21vw;
        height: auto;
      }

      &-four {
        bottom: 14.5vw;
        right: 34.5vw;
        width: 10vw;
        height: auto;
      }
    }
  }

  @media (max-width: 1850px) {
    &__line {
      display: none;
    }
  }
}
</style>
