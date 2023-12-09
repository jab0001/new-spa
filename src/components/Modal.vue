<template>
  <div class="modal">
    <h2 class="modal__title">The order is almost in courier's hands!</h2>
    <p class="modal__description">
      You will be redirected to your personal account to complete the order
      process
    </p>
    <button class="modal__btn" @click="clickButtonHandler">
      Make it happen
    </button>
    <svg
      class="modal__close"
      @click="closeModal"
      width="18"
      height="18"
      viewBox="0 0 18 18"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
    >
      <path
        fill-rule="evenodd"
        clip-rule="evenodd"
        d="M1.47162 1.46978C1.76452 1.17689 2.23939 1.17689 2.53228 1.46978L16.5313 15.4688C16.8242 15.7617 16.8242 16.2366 16.5313 16.5295C16.2384 16.8224 15.7636 16.8224 15.4707 16.5295L1.47162 2.53044C1.17873 2.23755 1.17873 1.76268 1.47162 1.46978Z"
        fill="#C3C2C1"
      />
      <path
        fill-rule="evenodd"
        clip-rule="evenodd"
        d="M16.5303 1.46978C16.8232 1.76268 16.8232 2.23755 16.5303 2.53044L2.53127 16.5295C2.23838 16.8224 1.7635 16.8224 1.47061 16.5295C1.17772 16.2366 1.17772 15.7617 1.47061 15.4688L15.4697 1.46978C15.7626 1.17689 16.2374 1.17689 16.5303 1.46978Z"
        fill="#C3C2C1"
      />
    </svg>
  </div>
</template>

<script>
import { Component, Vue } from "vue-property-decorator";

@Component({})
export default class Modal extends Vue {
  closeModal() {
    this.$emit("closeModal");
  }

  clickButtonHandler() {
    console.log("clickModalButton");
    this.closeModal();
  }
}
</script>

<style lang="scss" scoped>
.modal {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  padding: 33px;
  width: 343px;
  border-radius: 16px;
  background: #fff;

  box-sizing: border-box;

  &__title {
    font-family: "PollyRoundedRegular", "Open Sans";
    font-size: 24px;
    font-weight: 400;
    line-height: 29px;
    text-align: center;
  }

  &__description {
    margin-top: 16px;
    font-family: "PollyRoundedThin", "Open Sans";
    font-size: 16px;
    font-weight: 300;
    line-height: 22px;
    text-align: center;
  }

  &__btn {
    margin-top: 40px;
    padding: 19px;
    font-family: "PollyRoundedRegular", "Open Sans";
    font-size: 18px;
    font-weight: 400;
    line-height: 22px;
    text-align: center;
    border: none;
    border-radius: 30px;
    background: #112e95;
    width: 100%;
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

  &__close {
    position: absolute;
    top: 20px;
    right: 22px;

    cursor: pointer;

    &:hover {
      opacity: 0.5;
    }
  }

  @media (min-width: 768px) {
    width: 480px;
    padding: 40px;

    &__title {
      font-size: 32px;
      line-height: 38px;
    }

    &__description {
      font-size: 18px;
      line-height: 25px;
    }
  }
}
</style>
