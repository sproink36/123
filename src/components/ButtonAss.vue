<template>
  <!-- <div
    class="button"
    @mouseenter="isPure = false"
    :class="{
      green: btnType === 'green',
      black: btnType === 'black',
      pure: isPure,
    }"
  >
    <div class="content">
      <div class="background background__defualt"></div>
      <span class="text text__defualt">
        <slot></slot>
      </span>
      <div class="background background__new"></div>
      <span class="text text__new">
        <slot></slot>
      </span>
    </div>
  </div> -->
</template>

<script setup lang="js">
import gsap from "gsap";
import { onMounted, ref } from "vue";

const props = defineProps({
  btnType: String,
});

const isPure = ref(true);

// onMounted(() => {
//   tween = gsap.to(el,{rotation: 360, repeat: -1}) 
// });
</script>

<style lang="scss" scoped>
@use "/src/assets/scss/includes/common" as *;
@use "/src/assets/scss/includes/variables" as *;
@use "/src/assets/scss/includes/media-queries";
// & .anim_span {
//   position: absolute;
//   left: 0;
//   top: 100%;
//   width: 100%;
//   display: flex;
//   justify-content: center;
//   align-items: center;
//   height: 100%;
//   background-color: red;
// }

// .pure .anim_span,
// .pure .defualt_span {
//   animation: none;
// }

.button {
  @include button-style;
  height: 84px;
  overflow: hidden;
  cursor: pointer;

  &:hover .text__defualt {
    animation: text__defualt_up 0.25s forwards;
  }

  &:hover .background__defualt {
    animation: background__defualt_up 0.25s forwards;
  }

  &:hover .text__new {
    animation: text__new_up 1.25s forwards;
  }

  &:hover .background__new {
    animation: background__new_up 0.25s forwards;
  }

  &:not(:hover) .background__defualt {
    animation: background__defualt_dowm 1.25s forwards;
  }

  

  
}

@keyframes text__defualt_up {
  0% {
    top: 0;
  }

  100% {
    top: -100%;
  }
}

@keyframes background__defualt_up {
  0% {
    top: 0;
  }

  100% {
    top: -100%;
  }
}

@keyframes background__defualt_dowm {
  0% {
    top: 100%;
  }

  100% {
    top: 0;
  }
}

@keyframes text__new_up {
  0% {
    top: 100%;
  }

  100% {
    top: 0;
  }
}

@keyframes background__new_up {
  0% {
    top: 100%;
  }

  100% {
    top: 0;
  }
}

.content {
  position: absolute;
  width: 100%;
  height: 100%;
  overflow: hidden;
  z-index: 0;
}

.text,
.background {
  position: absolute;
  width: 100%;
  height: 100%;
}

.text {
  display: flex;
  align-items: center;
  justify-content: center;
  // transition: transform 0.5s ease;
  font-size: inherit;
  line-height: inherit;
  font-weight: inherit;
  z-index: 2;
}

.background__defualt,
.text__defualt {
  top: 0;
  left: 0;
}

.background__new,
.text__new {
  top: 100%;
  left: 0;
}

// .text__new {
//   top: 100%;
//   left: 0;
//   transform: translateY(100%);
//   opacity: 0;
// }

// .text__new.visible {
//   transform: translateY(0);
//   opacity: 1;
// }

.background {
  position: absolute;
  left: 0;
  width: 100%;
  height: 100%;
  transition: transform 0.5s ease;
  z-index: 1;
}

/* Исходный фон */
.background__defualt {
  top: 0;
}

.background__new {
  top: 100%;
  background-color: red;
}

// .background__defualt.hidden {
//   top: -100%;
// }

/* Новый фон */
// .background__new {
//   background-color: coral;
//   transform: translateY(100%);
// }

// .background__new.visible {
//   transform: translateY(0);
// }
</style>
