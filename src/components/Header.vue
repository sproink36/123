<template>
  <header class="header" :class="{ white_wall: isOpenBurger }">
    <div class="container header__container">
      <Logo class="header__logo" />
      <ul class="list" v-if="mediaLarge">
        <li class="item">
          <a class="link" ef="#">
            <span class="link_text link_defualt">Преимущества</span>
            <span class="link_text link_copy">Преимущества</span>
            <span class="link_hidden">Преимущества</span>
          </a>
        </li>
        <li class="item">
          <a class="link" ef="#">
            <span class="link_text link_defualt">Расширение/плагин</span>
            <span class="link_text link_copy">Расширение/плагин</span>
            <span class="link_hidden">Расширение/плагин</span>
          </a>
        </li>
        <li class="item">
          <a class="link" ef="#">
            <span class="link_text link_defualt">FAQ</span>
            <span class="link_text link_copy">FAQ</span>
            <span class="link_hidden">FAQ</span>
          </a>
        </li>
      </ul>
      <div class="block">
        <GenerateQRButton />
        <Button class="header__button" btnType="black">
          <template v-if="mediaLarge">Войти или зарегистрироваться</template>
          <User v-else />
        </Button>
      </div>
      <div
        class="burger-btn"
        v-if="!mediaLarge"
        :class="{ burger_open: isOpenBurger }"
        @click="toggleModal"
      >
        <div class="lines">
          <div class="line"></div>
        </div>
      </div>
    </div>
    <Teleport to="body">
      <Transition>
        <div class="burger-overlay" v-if="isOpenBurger && !mediaLarge">
          <div class="burger-menu" ref="burgerRef" id="burger-menu">
            <div class="container">
              <ul class="burger__list">
                <li class="burger__item" v-for="item in burgerList" :key="item">
                  <a href="#">{{ item }}</a>
                </li>
              </ul>
              <Button
                class="burger__btn"
                btnType="black"
              >
                Сгенерировать куаркод
              </Button>
              <div class="burger__links">
                <a href="#">Политика конфиденциальности</a>
                <a href="#">support@qrcode.ru</a>
                <a href="#">©куаркод.инк 2024</a>
              </div>
            </div>
          </div>
        </div>
      </Transition>
    </Teleport>
  </header>
</template>

<script setup>
import { Logo, User } from "../assets/icons";
import GenerateQRButton from "./GenerateQRButton.vue";
import Button from "./Button.vue";
import { useMedia } from "../hooks/useMedia";
import { onUpdated, ref, watch } from "vue";

const mediaLarge = useMedia("(min-width: 1520px)");
const isOpenBurger = ref(false);
const burgerList = [
  "Преимущества",
  "Расширение/плагин",
  "FAQ",
  "Вход/регистрация",
  "ВКонтакте",
  "Инстаграм",
];

const burgerRef = ref(null);

watch(mediaLarge, () => {
  if (mediaLarge.value && isOpenBurger.value) {
    isOpenBurger.value = false;
  }
});

watch(mediaLarge, () => {
  if (mediaLarge.value) {
    document.body.classList.remove("frozen");
  }
});

function toggleModal() {
  isOpenBurger.value = !isOpenBurger.value;
  document.body.classList.toggle("frozen");
  // add && mediaLarge.value
  if (isOpenBurger.value && mediaLarge.value) {
    window.scrollTo({
      top: 0,
      behavior: "smooth", // Плавная прокрутка
    });
  }
}

onUpdated(() => {});
</script>

<style lang="scss" scoped>
@use "/src/assets/scss/includes/common" as *;
@use "/src/assets/scss/includes/media-queries";
@use "/src/assets/scss/includes/variables" as *;

.header {
  width: 100%;
  // z-index: 60;
  background-color: white;
  position: relative;

  @include media-queries.media-large {
    margin-bottom: 112px;
  }

  @include media-queries.media-medium {
    margin: 0 auto 60px auto;
  }

  @include media-queries.media-small {
    margin: 0 auto 40px auto;
  }

  &.white_wall::after {
    content: "";
    height: 300px;
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: white;
    z-index: 40;
  }
}

.header__container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  @include media-queries.media-large {
    max-width: 1840px;
  }

  @include media-queries.media-medium {
    padding-bottom: 20px;
  }
}

.header__logo {
  z-index: 50;
  width: 100px;
  height: 100px;

  @include media-queries.media-small {
    width: 60px;
    height: 60px;
  }
}

.list {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 40px;
  height: 84px;
  padding: 0 30px;
  background-color: #f3f5f7;

  @include media-queries.media-large {
    margin-left: auto;
  }
}

.item {
  overflow: hidden;
}

.link {
  position: relative;
  // font-weight: 500;
  // font-size: 18px;
  // line-height: 133%;
  cursor: pointer;

  & .link_hidden {
    visibility: hidden;
  }

  & .link_text {
    position: absolute;
    left: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100%;
    font-weight: 500;
    font-size: 18px;
    line-height: 133%;
    transition: top 0.3s ease;
  }

  & .link_defualt {
    top: 0;
  }

  & .link_copy {
    top: 100%;
    color: #18213C99;
  }

  &:hover .link_defualt {
    top: -100%;
  }

  &:hover .link_copy {
    top: 0;
  }
}

.block {
  display: flex;
  gap: 10px;

  @include media-queries.media-large {
    margin-left: 190px;
  }

  @include media-queries.media-medium {
    gap: 16px;
  }

  @include media-queries.media-small {
  }
}

.header__button {
  @include media-queries.media-large {
    width: 379px;
  }

  @include media-queries.media-medium {
    @include circle;
    width: 100px;
    height: 100px;
  }

  @include media-queries.media-small {
    width: 60px;
    height: 60px;
  }
}

.burger-btn {
  @include circle;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100px;
  height: 100px;
  border-color: $black;
  background-color: white;
  cursor: pointer;
  z-index: 50;

  & .lines {
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 20px;
    width: 33px;

    & .line,
    &::after,
    &::before {
      content: "";
      position: absolute;
      left: 50%;
      display: block;
      width: 100%;
      height: 3.333px;
      background-color: $black;
      border-radius: 10px;
    }

    & .line {
      top: 50%;
      opacity: 1;
      transform: translate(-50%, -50%);
      transition: opacity 0.2s ease-in-out;
    }

    &::after {
      transform: translateX(-50%);
      transition: all 0.3s ease-in-out;
      top: 0;
    }

    &::before {
      transform: translateX(-50%);
      transition: all 0.3s ease-in-out;
      bottom: 0;
    }
  }

  &.burger_open .lines {
    & .line {
      opacity: 0;
    }

    &::after {
      top: 50%;
      transform: translate(-50%, -50%) rotateZ(45deg);
    }

    &::before {
      bottom: 50%;
      transform: translate(-50%, 50%) rotateZ(-45deg);
    }
  }

  @include media-queries.media-small {
    width: 60px;
    height: 60px;
  }
}

.burger-overlay {
  position: fixed;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  opacity: 1;
  z-index: 11;
}

.burger-menu {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: white;
  padding: 180px 0 40px 0;
  overflow-y: auto;
  scrollbar-width: none;
  &::-webkit-scrollbar {
    display: none;
  }
  & .burger__list {
    display: flex;
    flex-direction: column;
    gap: 40px;
    margin-bottom: 90px;

    & a {
      font-family: "PIXY";
      font-size: 48px;
      line-height: 116%;
    }
  }

  .burger__btn {
    margin-bottom: 50px;
  }

  & .burger__links {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 10px;

    & a {
      font-size: clamp(16px, 18px, 22px);
      font-weight: 500;
      line-height: 133%;
      color: rgba(38, 39, 42, 0.3);
    }
  }

  // @include media-queries.media-medium {
  //   margin-top: 180px;
  // }
  // @media (min-width: 768px) {
  //   padding: 180px 40px 40px 40px;
  // }

  @include media-queries.media-small {
    padding: 140px 20px 27px 20px;

    & .burger__list {
      margin-bottom: 40px;

      & a {
        font-size: 32px;
        line-height: 40px;
      }
    }

    & .burger__btn {
      margin-bottom: 40px;
    }

    & .burger__links {
      flex-direction: column;
      gap: 10px;

      & a {
        text-align: center;
      }
    }
  }
}

.v-enter-active,
.v-leave-active {
  left: 0;
  opacity: 1;
  transition: all 1s ease;
  pointer-events: all;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
  pointer-events: none;
  left: -100%;
}
</style>
