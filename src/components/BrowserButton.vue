<template>
  <div class="block" :class="{ disabled: disabled }">
    <Button class="btn" btnType="green"><slot></slot></Button>
    <Browser class="browser" />
  </div>
</template>

<script setup>
import Button from "./Button.vue";
import { Browser } from "../assets/icons";

defineProps({
  disabled: Boolean,
});
</script>

<style lang="scss" scoped>
@use "/src/assets/scss/includes/media-queries";
@use "/src/assets/scss/includes/variables" as *;
.block {
  position: relative;
  height: 84px;
  width: 100%;
  box-shadow: 0 0 0 2px $black;
  border-radius: 100px;
  align-self: center;

  &:hover .browser {
    fill: #0dc134;
  }

  &:active .browser {
    fill: #0eb231;
  }

  &:last-child {
    pointer-events: auto;
  }

  &.disabled {
    opacity: 20%;
    pointer-events: none;
  }

  @include media-queries.media-large {
    width: 391px;
  }

  @include media-queries.media-small {
    height: 64px;
  }

  & .btn {
    position: absolute;
    top: 0;
    left: 0;
    border: none;
    box-shadow: 0 0 0 2px $black;
    transition-property: width;
    @include media-queries.media-large {
      width: 297px;
    }

    @include media-queries.media-medium {
      width: 100%;
      min-width: 594px;
      max-width: calc(100% - 94px);
    }

    @include media-queries.media-small {
      width: 100%;
      min-width: 256px;
      max-width: calc(100% - 94px);
    }

    @media (max-width: 389px) {
      width: 70%;
      min-width: 156px;
      font-size: 12px;
    }
  }

  & .browser {
    position: absolute;
    top: 50%;
    right: 42.67px;
    transform: translateY(-50%);
    fill: $black;

    @media (max-width: 389px) {
      right: 15%;
    }
  }
}
</style>
