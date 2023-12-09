<template>
  <div class="service" id="carrying">
    <div class="service__desktop">
      <h2 class="service__title">
        Delivery service that perfectly matches your needs
      </h2>
      <ul class="service__list">
        <li class="service__item" v-for="card in cards" :key="card.title">
          <img
            class="service__img"
            width="343"
            height="183"
            :src="`../img/cards/${card.img}.jpg`"
            :alt="`image ${card.title}`"
          />
          <div class="service__container">
            <h3 class="service__title-item">{{ card.title }}</h3>
            <p class="service__description">{{ card.description }}</p>
            <a class="service__link" href="#calculator"
              >Calculate the cost<img src="@/assets/img/arrow.svg"
            /></a>
          </div>
        </li>
      </ul>
    </div>
    <div class="service__ellipse"></div>
    <img
      class="service__line service__line-one"
      src="../assets/img/lines/line-service-1.svg"
    />
    <img
      class="service__line service__line-two"
      src="../assets/img/lines/line-service-2.svg"
    />
    <img
      class="service__line service__line-three"
      src="../assets/img/lines/line-service-3.svg"
    />
  </div>
</template>

<script>
import { Component, Vue } from "vue-property-decorator";

@Component({})
export default class Service extends Vue {
  cards = [
    {
      img: "stores",
      title: "Online stores",
      description:
        "Quickly deliver any goods up to 1.5 tons and collect payment from recipients",
    },
    {
      img: "food",
      title: "Food & groceries",
      description:
        "Deliver orders to your customers in thermal bags to keep the temperature of your meals",
    },
    {
      img: "documents",
      title: "Documents",
      description:
        "Deliver documents in folders, wait for them to be signed, and bring them back",
    },
    {
      img: "pharmacy",
      title: "Pharmacy",
      description:
        "Deliver small bags of medications right to customers. Large boxes will be transported from the warehouse to the pharmacy",
    },
    {
      img: "clothes",
      title: "Clothes",
      description:
        "Deliver clothing and shoes for fittings and handle returns if needed",
    },
    {
      img: "anything",
      title: "Anything and everything",
      description:
        "Flowers, gifts, and any other cargo. We will fulfill all your wishes",
    },
  ];
}
</script>

<style lang="scss" scoped>
.service {
  padding: 40px 16px 36px 16px;
  background: #112e95;

  &__line {
    display: none;
  }

  &__ellipse {
    display: none;
  }

  &__title {
    font-family: "PollyRoundedRegular", "Open Sans";
    font-size: 40px;
    font-weight: 400;
    line-height: 42px;
    text-align: left;

    color: #fff;

    &-item {
      font-family: "PollyRoundedRegular", "Open Sans";
      font-size: 24px;
      font-weight: 400;
      line-height: 32px;
      text-align: left;

      letter-spacing: -0.7px;

      color: #18191d;
    }
  }

  &__img {
    width: 100%;
    height: auto;
    object-fit: cover;
    min-height: 182px;
  }

  &__list {
    margin-top: 32px;
  }

  &__item {
    background: #fff;
    border-radius: 16px;
    overflow: hidden;
    min-height: 410px;

    &:not(:first-child) {
      margin-top: 20px;
    }
  }

  &__container {
    padding: 20px;
    min-height: 180px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  &__description {
    margin-top: 12px;

    font-family: "PollyRoundedThin", "Open Sans";
    font-size: 16px;
    font-weight: 300;
    line-height: 24px;
    text-align: left;

    color: #18191d;
  }

  &__link {
    display: flex;
    text-decoration: none;
    width: fit-content;

    margin-top: auto;

    font-family: "PollyRoundedRegular", "Open Sans";
    font-size: 16px;
    font-weight: 400;
    line-height: 22px;
    text-align: left;

    color: #112e95;

    img {
      margin-left: 10px;
    }

    &:hover {
      opacity: 0.7;
    }

    &:active {
      color: #0c247d;
    }
  }

  @media (min-width: 768px) {
    padding-top: 92px;
    padding-left: 13px;
    padding-right: 13px;
    padding-bottom: 97px;
    position: relative;
    overflow: hidden;

    &__ellipse {
      display: block;
      position: absolute;
      width: 80%;
      height: 70%;
      top: 50%;
      left: 50%;
      border-radius: 50%;
      transform: translate(-50%, -25%);
      background: radial-gradient(ellipse at center, #fff 0%, #112e95 65%);
    }

    &__desktop {
      max-width: 1180px;
      margin: 0 auto;
      z-index: 1;
      position: relative;
    }

    &__title {
      font-size: 64px;
      line-height: 68px;

      &-item {
        font-size: 28px;
        letter-spacing: initial;
      }
    }

    &__description {
      margin-top: 16px;
      font-size: 18px;
    }

    &__link {
      font-size: 18px;
    }

    &__container {
      padding-top: 15px;
      min-height: 185px;
    }

    &__list {
      margin-top: 130px;

      display: flex;
      flex-wrap: wrap;
      gap: 26px 20px;
      justify-content: center;
    }

    &__item {
      max-width: 379px;
      max-height: 416px;

      &:not(:first-child) {
        margin-top: 0px;
      }
    }

    &__line {
      display: block;
      position: absolute;

      &-one {
        top: 0;
        left: 0;

        width: 26vw;
        height: auto;
      }

      &-two {
        top: -15px;
        right: 0;
        width: 24vw;
        height: auto;
      }

      &-three {
        bottom: -6.5vw;
        right: 0.5vw;
        width: 15vw;
        height: auto;
      }
    }
  }

  @media (min-width: 768px) and (max-width: 1265px) {
    &__line {
      &-two {
        width: 30vw;
        top: 19vw;
      }
    }
  }
}
</style>
