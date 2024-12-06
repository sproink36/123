<template>
  <div class="card" @click="isOpen = !isOpen" :class="{ active: isOpen }">
    <div class="header">
      <H4Title class="title">{{ title }}</H4Title>
      <div class="circle">
        <Angle />
      </div>
    </div>
    <p class="text">
      {{ text }}
    </p>
  </div>
</template>

<script setup lang="js">
import H4Title from "./H4Title.vue";
import { Angle } from "../assets/icons/index";
import { ref } from "vue";
defineProps({
  title: String,
  text: String,
})

const isOpen = ref(false);
</script>

<style lang="scss" scoped>
@use "/src/assets/scss/includes/media-queries";
@use "/src/assets/scss/includes/variables" as *;

.card {
  background-color: #f3f5f7;
  border-radius: 40px;
  display: flex;
  flex-direction: column;
  border: 2px solid #F3F5F7;
  cursor: pointer;

  &:hover {

    border: 2px solid #18213C33;
  }

  &.active {
    background-color: #e3e7eb;
  }

  @include media-queries.media-large {
    padding: 60px;
  }

  @include media-queries.media-medium {
    padding: 30px;
  }

  @include media-queries.media-small {
    padding: 20px;
  }

  .header {
    display: flex;
    justify-content: space-between;
  }

  .circle {
    width: 48px;
    height: 48px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 50%;
    border: 2px solid $black;
    transform: rotateZ(180deg);
    transition: transform 0.5s ease;
    flex-shrink: 0;



    &>* {
      width: 100%;
      height: 100%;
    }

    @include media-queries.media-small {
      width: 32px;
      height: 32px;
    }
  }

  .text {
    opacity: 0;
    max-height: 0;
    overflow: hidden;
    padding-top: 0;
    transition: all 0.5s;
    font-size: 24px;
    font-weight: 400;
    line-height: 32px;
    text-align: left;

    @include media-queries.media-small {
      font-size: 14px;
    }
  }

  &.active .text {
    opacity: 1;
    padding-top: 20px;

    @include media-queries.media-large {
      max-height: 400px;
    }

    @include media-queries.media-medium {
      max-height: 700px;
    }

    @include media-queries.media-small {
      max-height: 800px;
    }
  }

  &.active .circle {
    transform: rotateZ(0deg);
  }
}
</style>
