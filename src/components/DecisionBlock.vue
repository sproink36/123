<script setup lang="ts">
import H2Title from "./H2Title.vue";
import saveKuarCod from "/src/assets/img/saveKuarCod.png"
import quarCodBlock from "/src/assets/img/quarCodBlock.png"
</script>

<template>
  <div class="block">
    <div class="container block_container">
      <img class="saveKuarCod" :src="saveKuarCod" alt="сохранить куаркод" />
      <div class="wrapper_img">
        <img class="quarCodBlock" :src="quarCodBlock" />
      </div>
      <img class="vector" src="/src/assets/img/Vector 1.png" />
      <img class="vector_mini" src="/src/assets/img/Vector1mini.png" />
      <H2Title class="title">
        Преобразуем<br />
        привычные действия <br />
        в удобные решения!
      </H2Title>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@use "/src/assets/scss/includes/media-queries";

.block {
  width: 100%;
  display: flex;
  justify-content: center;

  @include media-queries.media-large {
    height: 822px;
  }

  @include media-queries.media-medium {
    height: 516px;
  }

  @include media-queries.media-small {
    height: 250px;
  }
}

.block_container {
  position: relative;

  @include media-queries.media-large {
    padding-top: 198px;
  }

  @include media-queries.media-medium {
    padding-top: 103px;
  }

  @include media-queries.media-small {
    padding-top: 42px;
  }
}

img {
  position: absolute;
  z-index: -50;
}

.saveKuarCod {
  @include media-queries.media-large {
    top: -40px;
    left: -20px;
  }

  @include media-queries.media-medium {
    width: 317px;
    height: 317px;
    top: -30px;
    left: -162px;
  }

  @include media-queries.media-small {
    width: 139px;
    height: 139px;
    top: -15px;
    left: -52px;
    z-index: 10;
  }
}

.wrapper_img {
  position: absolute;
  overflow: hidden;
  right: 0;

  @include media-queries.media-large {
    width: 400px;
    height: 400px;
    bottom: 41px;
    right: -32px;
  }

  @include media-queries.media-medium {
    width: 200px;
    height: 200px;
    bottom: 27px;
    right: -12px;
  }

  @include media-queries.media-small {
    width: 70px;
    height: 70px;
    // right: 0;
    bottom: 46px;
  }
}

.quarCodBlock {
  // transform: scale(1.6);
  top: 0;
  left: 0;

  // @include media-queries.media-large {
  //   // right: 120px;
  // }

  // @include media-queries.media-medium {
  //   top: -20px;
  //   right: 10px;
  // }

  // @include media-queries.media-small {
  //   left: -15px;
  //   top: -5px;
  //   transform: scale(2);
  // }
}

.vector {
  max-width: 100%;

  transform: translate(-50%);
  z-index: -100;
  top: 0;
  left: 50%;

  @include media-queries.media-small {
    display: none;
  }
}

.vector_mini {
  max-width: 100%;
  display: none;
  transform: translate(-50%);
  z-index: -100;
  top: 0;
  left: 50%;

  @include media-queries.media-small {
    display: block;
  }
}

.title {
  & br:first-child {
    @include media-queries.media-small {
      display: none;
    }
  }

  & br:last-child {
    display: none;

    @include media-queries.media-small {
      display: block;
    }
  }
}
</style>
