<template>
  <div class="select" :data-value="value" :data-list="list">
    <input
      class="select__input"
      placeholder="What do we deliver"
      :value="value"
      @input="(evt) => select(evt, true)"
    />
    <ul class="select__list">
      <li
        :class="`select__item ${item === value ? 'current' : ''}`"
        v-for="(item, index) in list"
        :key="index"
        @click="(evt) => select(evt, false, item)"
      >
        {{ item }}
      </li>
    </ul>
  </div>
</template>

<script>
import { Component, Vue } from "vue-property-decorator";

@Component({})
export default class SelectInput extends Vue {
  value = "";
  list = [
    "Grocery & food",
    "Pharmacy",
    "Bakery",
    "Documents",
    "Clothes",
    "Flowers",
    "Cake",
    "Guitar",
    "Coffee maker",
    "Other",
  ];

  select(evt, type, value) {
    if (type) {
      this.value = evt.target.value;
      this.$emit("updateDelivery", evt.target.value);
      return;
    }
    this.value = value;
    this.$emit("updateDelivery", this.value);
  }
}
</script>

<style lang="scss" scoped>
.select {
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
    padding: 15px 15px 15px 17px;
    border: 1.5px solid #ebebea;
    border-radius: 12px;
    box-sizing: border-box;
  }

  &__list {
    padding: 0;
    margin-top: 12px;
    display: flex;
    width: 100%;
    overflow: auto;
    -ms-overflow-style: none;
    scrollbar-width: none;

    &::-webkit-scrollbar {
      width: 0;
      height: 0;
    }
  }

  &__item {
    font-family: "PollyRoundedRegular", "Open Sans";
    font-size: 16px;
    font-weight: 400;
    line-height: 22px;
    text-align: left;
    white-space: nowrap;

    color: #112e95;

    cursor: pointer;

    &:not(:last-child) {
      margin-right: 16px;
    }

    &:hover {
      opacity: 0.7;
    }
  }
  .current {
    font-family: "PollyRoundedBold", "Open Sans";
    font-weight: 700;
    color: #0c247d;
  }

  @media (min-width: 768px) {
    &__item {
      &:not(:last-child) {
        margin-right: 32px;
      }
    }
  }
}
</style>
