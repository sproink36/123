<script setup lang="ts">
import H2Title from "./H2Title.vue";
</script>

<template>
  <div class="block">
    <div class="container block_container">
      <img
        class="saveKuarCod"
        src="/src/assets/img/saveKuarCod.png"
        alt="сохранить куаркод"
      />
      <!-- <img class="quarCodBlock" src="/src/assets/img/quarCodBlock.png" /> -->
      <img class="vector" src="/src/assets/img/Vector 1.png" />
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
    height: 280px;
  }
}

// .img_container {
//   position: relative;
//   padding-top: 220px;
//   width: 1560px;
//   transform: translateX(-50%);

//   @include media-queries.media-medium {
//     padding-top: 150px;
//   }

//   @include media-queries.media-small {
//     padding-top: 80px;
//   }
// }

.block_container {
  position: relative;
  padding-top: 220px;
}

img {
  position: absolute;
  z-index: -50;
}

.saveKuarCod {
  top: 0;

  @include media-queries.media-large {
    left: -20px;
  }

  @include media-queries.media-medium {
    width: 317px;
    height: 317px;
    top: -20px;
    // left: clamp();
    // transform: translateX(-40%);
  }

  @include media-queries.media-small {
    width: 139px;
    height: 139px;
  }
}

.quarCodBlock {
  right: 0;
  top: 110px;
  transform: translateX(30%) rotateZ(18.71deg);
}

.vector {
  max-width: 100%;
  top: 0;
  left: 50%;
  transform: translate(-50%);
  z-index: -100;

  @include media-queries.media-medium {
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
