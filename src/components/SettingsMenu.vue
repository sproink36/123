<template>
  <div class="settings_menu" :class="{ active: isOpen }">
    <div class="header" @click="isOpen = !isOpen">
      <div class="block">
        <div class="icon"><slot name="icon"></slot></div>
        <p class="title"><slot name="title"></slot></p>
      </div>
      <div class="icon_angle">
        <Angle1 />
      </div>
    </div>
    <div class="container_cont">
      <div class="content">
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import Angle1 from "../assets/icons/Angle1.vue";
const isOpen = ref(false);
</script>

<style lang="scss" scoped>
.settings_menu {
  padding: 20px;
  display: flex;
  flex-direction: column;
  width: 100%;
  border: 2px solid #18213c;
  border-radius: 30px;
  overflow: hidden;

  .header {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    cursor: pointer;
  }

  .block {
    display: flex;
    gap: 10px;
  }

  .icon_angle {
    width: 32px;
    height: 32px;
    transition: transform 0.5s;

    & > * {
      width: 100%;
      height: 100%;
    }
  }

  .content {
    max-height: 0;
    opacity: 0;
    padding-top: 0;
    overflow: hidden;
    transition: all 0.5s;
  }
}

.settings_menu.active {
  & .icon_angle {
    transform: rotateZ(-180deg);
  }

  & .content {
    max-height: 328px;
    padding-top: 20px;
    opacity: 1;
  }
}
</style>
