<template>
  <div class="order">
    <div class="order__container">
      <div>
        <h2 class="order__title">Place your 1st order for delivery</h2>
        <p class="order__description">
          You need to do just a few clicks, and we will do the rest
        </p>
      </div>
      <button class="order__btn" @click="clickHandler">
        Calculate the cost
      </button>
    </div>
  </div>
</template>

<script>
import { Component, Vue } from "vue-property-decorator";

@Component({})
export default class FirstOrder extends Vue {
  clickHandler() {
    const element = document.querySelector("#calculator");
    let top = element.offsetTop;

    window.scrollTo(0, top);
  }
}
</script>

<style lang="scss" scoped>
.order {
  background: #122f96;
  padding: 40px 16px;

  &__container {
    border-radius: 16px;
    padding: 24px;

    background: #fff;
  }

  &__title {
    font-family: "PollyRoundedRegular", "Open Sans";
    font-size: 32px;
    font-weight: 400;
    line-height: 35px;
    text-align: center;

    color: #18191d;
  }

  &__description {
    margin-top: 16px;
    font-family: "PollyRoundedThin", "Open Sans";
    font-size: 16px;
    font-weight: 300;
    line-height: 22px;
    text-align: center;

    color: #18191d;
  }

  &__btn {
    margin-top: 24px;
    padding: 19px 60px;

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
    padding: 80px 16px;

    &__container {
      max-width: 1179px;
      margin: 0 auto;
      padding: 74px 100px;
      box-sizing: border-box;
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
    }

    &__btn {
      margin: 0;
      padding: 0px 48px;
      height: 60px;
    }

    &__title {
      font-size: 36px;
      line-height: 36px;
    }

    &__description {
      margin-top: 18px;
      font-size: 18px;
      line-height: 24px;

      text-align: left;
    }
  }
}
</style>
