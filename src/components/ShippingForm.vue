<template>
  <div class="shipping" id="calculator">
    <h2 class="shipping__title">Calculate shipping cost</h2>
    <form class="shipping__form">
      <div class="shipping__container">
        <h3 class="shipping__title-item">Select delivery time</h3>
        <ul class="shipping__list">
          <li
            class="shipping__item shipping__item-delivery"
            v-for="delivery in deliveryTimes"
            :key="delivery.id"
          >
            <input
              class="shipping__input-radio"
              type="radio"
              :value="delivery.value"
              v-model="formModel.deliveryTime"
              name="deliveryTime"
              :id="delivery.title"
            />
            <label class="shipping__label" :for="delivery.title">
              <div
                class="shipping__circle"
                :style="`background: ${delivery.imgColor}`"
              >
                <img
                  class="shipping__img"
                  :src="`../img/cards/${delivery.img}.svg`"
                />
              </div>
              <h4 class="shipping__title-card">{{ delivery.title }}</h4>
              <p class="shipping__text">{{ delivery.text }}</p>
              <p class="shipping__description shipping__description-delivery">
                from {{ delivery.price }} $
              </p>
            </label>
          </li>
        </ul>
      </div>
      <div class="shipping__container">
        <h3 class="shipping__title-item">Parcel weight</h3>
        <ul class="shipping__list">
          <li
            class="shipping__item shipping__item-weight"
            v-for="weight in deliveryWeights"
            :key="weight.id"
          >
            <input
              class="shipping__input-radio"
              type="radio"
              :value="weight.value"
              v-model="formModel.deliveryWeight"
              name="deliveryWeight"
              :id="weight.title"
            />
            <label
              class="shipping__label shipping__label-desktop"
              :for="weight.title"
            >
              <div
                class="shipping__circle"
                :style="`background: ${weight.imgColor}`"
              >
                <img
                  class="shipping__img"
                  :src="`../img/cards/${weight.img}.svg`"
                />
              </div>
              <h4 class="shipping__title-card">{{ weight.title }}</h4>
              <p class="shipping__description shipping__description-weight">
                {{ weight.description }}
              </p>
            </label>
          </li>
        </ul>
      </div>
      <div class="shipping__container">
        <h3 class="shipping__title-item">Addresses</h3>
        <ul class="shipping__list-address">
          <li
            class="shipping__item-address"
            v-for="(input, index) in inputs"
            :key="index"
          >
            <img
              class="shipping__line"
              :style="inputs.length === index + 1 ? 'display: none;' : ''"
              src="../assets/img/line.svg"
            />
            <div
              :style="
                index > 1
                  ? 'display: flex; justify-content: space-between;'
                  : ''
              "
            >
              <h4 class="shipping__title shipping__title-address">
                {{ index === 0 ? "Sender" : "Recipient" }}
              </h4>
              <button
                v-if="index > 1"
                href=""
                class="shipping__remove"
                @click="(evt) => removeAddressHandler(evt, index)"
              >
                Delete
              </button>
            </div>
            <div class="shipping__address">
              <AddressInput
                v-for="(addressInput, index) in input"
                :key="index"
                :item="addressInput"
                :section="`shipping`"
              />
            </div>
          </li>
          <div class="shipping__inform-wrapper">
            <button
              :disabled="isDisabled"
              class="shipping__add"
              @click="addAddressHandler"
            >
              <img class="shipping__add-img" src="@/assets/img/add.svg" />Add
              address
            </button>
            <p class="shipping__information" v-if="isDisabled">
              Maximum number of recipients 15
            </p>
          </div>
        </ul>
      </div>
      <div class="shipping__container">
        <h3 class="shipping__title-item">What do we deliver</h3>
        <div class="shipping__wrapper">
          <SelectInput @updateDelivery="updateDelivery" />
        </div>
      </div>
      <div class="shipping__container">
        <h3 class="shipping__title-item">Total cost</h3>
        <div class="shipping__wrapper">
          <h4 class="shipping__title shipping__title-total">
            Total cost: from xxxx $
          </h4>
          <button
            class="shipping__btn"
            type="submit"
            @click="submitButtonHandler"
          >
            Place the order
          </button>
          <p class="shipping__description shipping__description-total">
            By signing up, I agree to Qwqer's
            <a href="" target="_blank" class="shipping__link">Privacy</a> and
            <a href="" target="_blank" class="shipping__link">Terms</a>
          </p>
        </div>
      </div>
    </form>
    <div></div>
  </div>
</template>

<script>
import { Component, Vue, Prop, Watch } from "vue-property-decorator";
import AddressInput from "@/components/Inputs/AddressInput.vue";
import SelectInput from "@/components/Inputs/SelectInput.vue";

@Component({
  components: {
    AddressInput,
    SelectInput,
  },
})
export default class ShippingForm extends Vue {
  @Prop({ type: Object, default: () => ({}) }) items;

  formModel = {
    deliveryTime: "",
    deliveryWeight: "",
    deliveryCategory: "",
    addresses: [],
  };
  isDisabled = false;
  maxRecipientAddresses = 15;
  inputs = [
    {
      address: {
        value: "",
        placeholder: "Sender address",
        name: "senderAddress",
        img: true,
      },
      phone: {
        value: "",
        placeholder: "Enter contact mobile number",
        name: "senderPhone",
        img: false,
      },
    },
    {
      address: {
        value: "",
        placeholder: "Recipient address",
        name: "recipientAddress",
        img: true,
      },
      phone: {
        value: "",
        placeholder: "Enter contact mobile number",
        name: "recipientPhone",
        img: false,
      },
    },
  ];

  deliveryTimes = [
    {
      id: 1,
      img: "time",
      imgColor: "#EBEBEA",
      title: "As soon as possible",
      text: "The order will be collected and delivered by the nearest available courier.",
      value: "soon",
      price: "xxx",
    },
    {
      id: 2,
      img: "calendar",
      imgColor: "#EBEBEA",
      title: "Schedule",
      text: "The courier will be at the addresses at a time convenient for you.",
      value: "schedule",
      price: "xxx",
    },
  ];
  deliveryWeights = [
    {
      id: 1,
      img: "envelope",
      imgColor: "#D6E4EE",
      title: "Envelope",
      description: "",
      value: "envelop",
    },
    {
      id: 2,
      img: "smallParcel",
      imgColor: "#E6DEED",
      title: "Small Parcel",
      description: "Cake, shoebox, soccer ball you.",
      value: "smallParcel",
    },
    {
      id: 3,
      img: "mediumParcel",
      imgColor: "#FAEDCC",
      title: "Medium Parcel",
      description: "Guitar, printer, coffee maker",
      value: "mediumParcel",
    },
    {
      id: 4,
      img: "largeParcel",
      imgColor: "#DEECDC",
      title: "Large Parcel",
      description: "Luggage, bicycle",
      value: "largeParcel",
    },
  ];

  @Watch("inputs", { immediate: true, deep: true })
  onInputChanged(val) {
    this.formModel.addresses = [];
    val.map((item) => {
      this.formModel.addresses.push({
        address: item.address.value,
        phone: item.phone.value,
      });
    });
    this.isDisabled =
      this.formModel.addresses.length >= this.maxRecipientAddresses;
  }

  @Watch("items", { immediate: true, deep: true })
  onInputUpdated(val) {
    this.inputs[0].address.value = val.sender;
    this.inputs[1].address.value = val.recipient;
  }

  updateDelivery(value) {
    this.formModel.deliveryCategory = value;
  }

  addAddressHandler(event) {
    event.preventDefault();
    this.inputs.push({
      address: {
        value: "",
        placeholder: "Recipient address",
        name: "recipientAddress",
        img: true,
      },
      phone: {
        value: "",
        placeholder: "Enter contact mobile number",
        name: "recipientPhone",
        img: false,
      },
    });
  }

  removeAddressHandler(evt, index) {
    evt.preventDefault();
    this.inputs.splice(index, 1);
  }

  submitButtonHandler(evt) {
    evt.preventDefault();
    console.log("submit");

    this.$emit("openModal");
  }
}
</script>

<style lang="scss" scoped>
.shipping {
  padding: 40px 0;
  background: rgba(32, 167, 165, 0.1);

  &__information {
    margin-top: 8px;
    font-family: "PollyRoundedThin", "Open Sans";
    font-size: 14px;
    font-weight: 300;
    line-height: 20px;
    text-align: left;

    color: #6e6d69;
  }

  &__text {
    display: none;
  }

  &__wrapper {
    background: #fff;
    border-radius: 16px;
    padding: 16px;
    margin-top: 10px;
  }

  &__link {
    text-decoration: none;
    font-family: "PollyRoundedBold", "Open Sans";
    color: #18191d;

    &:hover {
      opacity: 0.5;
    }
  }

  &__btn {
    margin-top: 19px;
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

  &__title {
    font-family: "PollyRoundedRegular", "Open Sans";
    font-size: 36px;
    font-weight: 400;
    line-height: 43px;
    text-align: center;

    color: #18191d;

    &-item {
      padding-left: 4vw;

      font-family: "PollyRoundedThin", "Open Sans";
      font-size: 18px;
      font-weight: 300;
      line-height: 32px;
      text-align: left;
      letter-spacing: 0.2px;

      color: #18191d;
    }

    &-card {
      margin-top: 16px;

      font-family: "PollyRoundedRegular", "Open Sans";
      font-size: 24px;
      font-weight: 400;
      line-height: 29px;
      text-align: left;

      color: #18191d;
    }

    &-address {
      font-size: 18px;
      text-align: left;
      line-height: 22px;
      margin-bottom: 12px;
    }

    &-total {
      font-size: 24px;
      line-height: 32px;
      text-align: left;
    }
  }

  &__description {
    font-family: "PollyRoundedThin", "Open Sans";
    font-weight: 300;
    text-align: left;

    &-delivery {
      margin-top: auto;

      font-size: 28px;

      line-height: 31px;
    }

    &-weight {
      margin-top: 12px;

      font-size: 16px;

      line-height: 22px;
    }

    &-total {
      margin-top: 12px;
      font-size: 16px;
      line-height: 20px;
    }
  }

  &__container {
    margin-top: 40px;

    &:not(:first-child) {
      margin-top: 32px;
    }
  }

  &__list {
    background: #fff;
    border-radius: 16px;
    display: flex;
    padding: 16px;
    margin-top: 8px;
    overflow: auto;
    gap: 16px;
    -ms-overflow-style: none;
    scrollbar-width: none;

    &::-webkit-scrollbar {
      width: 0;
      height: 0;
    }

    &-address {
      margin-top: 8px;
      padding: 17px 16px 18px 16px;
      background: #fff;
      border-radius: 16px;
    }
  }

  &__item {
    &-delivery {
      min-width: 212px;
      min-height: 193px;
    }

    &-weight {
      min-width: 216px;
      min-height: 177px;
    }

    &-address {
      &:not(:first-child) {
        margin-top: 16px;
      }
    }
  }

  &__label {
    display: flex;
    flex-direction: column;
    height: 100%;
    border: 1.5px solid #f5f5f5;
    border-radius: 16px;
    box-sizing: border-box;
    padding: 15px;

    cursor: pointer;

    &:hover {
      border: 1.5px solid #cccdd7;
    }
  }

  &__circle {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 40px;
    height: 40px;
    border-radius: 50%;
  }

  &__img {
    filter: brightness(0%);
  }

  &__line {
    display: none;
  }

  &__input {
    &-radio {
      display: none;

      &:checked + .shipping__label {
        border-color: #112e95;

        .shipping__img {
          filter: brightness(100%);
        }

        .shipping__circle {
          background: #112e95 !important;
        }
      }
    }
  }

  &__add,
  &__remove {
    padding: 0;
    margin-top: 20px;
    display: flex;
    align-items: center;
    font-family: "PollyRoundedRegular", "Open Sans";
    font-size: 18px;
    font-weight: 400;
    line-height: 22px;
    text-align: left;

    border: none;
    background: initial;

    text-decoration: none;

    color: #112e95;

    cursor: pointer;

    &-img {
      margin-right: 10px;
    }

    &:disabled {
      opacity: 0.4;
    }

    &:hover {
      opacity: 0.7;
    }

    &:active {
      color: #0c247d;
    }
  }

  &__remove {
    margin: 0;
  }

  @media (min-width: 768px) {
    padding-top: 95px;
    padding-bottom: 115px;

    &__inform-wrapper {
      display: flex;
      justify-content: space-between;
    }

    &__information {
      font-size: 16px;
      line-height: 20px;
    }

    &__title {
      font-size: 64px;
      line-height: 68px;

      &-item {
        padding: 0;
        font-size: 28px;
        line-height: 32px;
      }

      &-card {
        font-size: 27px;
        line-height: 32px;
      }

      &-address {
        font-size: 18px;
        line-height: 22px;
        margin-bottom: 0;
      }

      &-total {
        font-size: 32px;
        line-height: 32px;
      }
    }

    &__form {
      max-width: 1180px;
      margin: 0 auto;
    }

    &__container {
      margin-top: 80px;

      &:not(:first-child) {
        margin-top: 60px;
      }
    }

    &__list {
      margin-top: 20px;
      padding: 40px;
      flex-wrap: wrap;
      justify-content: center;

      &-address {
        margin-top: 20px;
        padding: 40px;
      }
    }

    &__item {
      &-address {
        padding-left: 42px;
        position: relative;

        &:first-child {
          &:after {
            border-color: #ad008c;
          }
        }

        &:after {
          content: "";
          position: absolute;
          top: 0;
          left: 0;
          width: 14px;
          height: 14px;
          border-radius: 50%;
          border: 4px solid #112e95;
        }

        &:not(:last-child) {
          padding-bottom: 25px;
        }

        &:not(:first-child) {
          margin-top: 0;
        }
      }
    }

    &__circle {
      width: 60px;
      height: 60px;
    }

    &__img {
      width: 32px;
      height: 32px;
    }

    &__label {
      padding: 24px;
      max-width: 540px;
      box-sizing: border-box;

      &-desktop {
        height: 224px;
        width: 261px;
      }
    }

    &__text {
      display: block;

      max-width: 492px;

      margin-top: 16px;

      font-family: "PollyRoundedThin", "Open Sans";
      font-size: 18px;
      font-weight: 300;
      line-height: 24px;
      text-align: left;
    }

    &__description {
      &-delivery {
        margin-top: 20px;
        font-size: 32px;
        line-height: 42px;
      }

      &-weight {
        margin-top: 20px;
      }

      &-total {
        margin-top: 20px;
        letter-spacing: -1.3px;
      }
    }

    &__address {
      display: flex;
      margin-top: 20px;
      justify-content: space-between;
    }

    &__add {
      padding-left: 42px;
      margin-top: 5px;
    }

    &__line {
      display: block;
      position: absolute;
      left: 5px;
      bottom: 5px;
    }

    &__wrapper {
      margin-top: 23px;
      padding: 40px;
    }

    &__btn {
      margin-top: 30px;
      max-width: 272px;
    }
  }
}
</style>
