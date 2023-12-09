<template>
  <label :class="`address__label address__label-${section}`" :for="item.name">
    <input
      v-model="item.value"
      :placeholder="item.placeholder"
      class="address__input"
      :name="item.name"
      :id="item.name"
      type="text"
    />
    <img v-if="item.img" class="address__geo" src="@/assets/img/geo.png" />
  </label>
</template>

<script>
import { Component, Prop, Vue } from "vue-property-decorator";

@Component({})
export default class AddressInput extends Vue {
  @Prop({ type: Object, default: () => ({}) }) item;
  @Prop({ type: String, default: "" }) section;
}
</script>

<style lang="scss" scoped>
.address {
  &__input {
    font-family: "PollyRoundedRegular", "Open Sans";
    font-size: 16px;
    font-weight: 400;
    line-height: 20px;
    text-align: left;
    border: none;
    outline: none;

    color: #6e6d69;

    width: 100%;

    padding: 15px 50px 15px 17px;
    border: 1.5px solid #ebebea;
    border-radius: 12px;

    &:focus {
      border-color: #18191d;
    }
  }

  &__geo {
    position: absolute;
    top: 16px;
    right: 19px;
    width: 19px;
    height: 21.5px;
  }

  &__label {
    display: flex;
    justify-content: space-between;
    box-sizing: border-box;
    position: relative;

    &:not(:first-child) {
      margin-top: 13px;
    }

    &-introduction:not(:first-child) {
      @media (min-width: 768px) {
        margin-top: 20px;
      }
    }

    @media (min-width: 768px) {
      &-shipping {
        width: 49%;

        &:not(:first-child) {
          @media (min-width: 768px) {
            margin-top: 0px;
          }
        }
      }
    }
  }
}
</style>
