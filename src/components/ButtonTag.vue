<template>
  <div class="block" :class="{ active: isSelect }">
    <p><slot name="text"></slot></p>
    <div class="icon"><slot name="icon"></slot></div>
  </div>
</template>

<script setup>
defineProps({
  isSelect: Boolean,
});
</script>

<style lang="scss" scoped>
@use "/src/assets/scss/includes/media-queries";

.block {
  text-wrap: nowrap;
  background-color: transparent;
  border: 2px solid #18213c;
  border-radius: 100px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: max-content;
  gap: 10px;
  cursor: pointer;
  padding: 15px 30px;

  & .icon {
    width: 24px;
    height: 24px;

    & > * {
      width: 100%;
      height: 100%;
      fill: #18213c;
    }
  }

  & p {
    text-align: left;
    color: #18213c;
    font-weight: 500;
    font-size: 24px;
    line-height: 32px;
  }

  @include media-queries.media-small {
    padding: 10px 20px;

    & p {
      font-size: 15px;
    }
  }
}

.block.active {
  background-color: #18213c;

  & p {
    color: white;
  }

  & .icon {
    & > * {
      fill: white;
    }
  }
}
</style>
