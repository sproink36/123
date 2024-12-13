<template>
  <div class="benefits">
    <div class="container">
      <H2Title class="title">Наши преимущества</H2Title>
      <div class="block">
        <BenefitsCard
          v-for="(item, index) in data"
          :key="item.bgColor"
          :bgColor="item.bgColor"
          :title="item.title"
          :text="item.text"
          :imgSRC="item.imgSRC"
          class="block__card_anim"
        >
          <Vue3Lottie
            :animationData="item.Loader"
            :height="'100%'"
            :width="'100%'"
          />
        </BenefitsCard>
        <div class="end"></div>
      </div>
    </div>
  </div>
</template>

<script lang="js" setup>
import BenefitsCard from "./BenefitsCard.vue";
import H2Title from "./H2Title.vue";
// import img1 from "../assets/img/Ill01.png";
import img2 from "../assets/img/Ill02.png"
// import img3 from "../assets/img/Ill03.png"
// import img4 from "../assets/img/Ill04.png"
import { Vue3Lottie } from 'vue3-lottie'
import twoBlocks from '../animations/twoBlocksQr.json'
import qr from '../animations/twoQRBlock.json'
import coin from '../animations/coin.json'
import { onMounted, ref } from "vue";
import gsap from "gsap";
import { ScrollTrigger } from "gsap/all";
import { ScrollToPlugin } from "gsap/all";

const data = [
    {bgColor: "#E5F2FF",title:"QR-коды с креативным подходом", text: "Создавайте оригинальные QR-коды, которые выделяются и подчеркивают ваш стиль. Простота, удобство и креативность в одном решении.", Loader: twoBlocks},
    {bgColor: "#FFF3DE",title:"Вся статистика— в одном месте", text: "Удобно собирайте и анализируйте данные о QR-кодах в одном месте. Все нужные метрики всегда под рукой.", imgSRC: img2},
    {bgColor:"#FBFFE3", title:"Ведите проекты без лишних забот",text:"Управляйте проектами легко и без стресса. Все инструменты под рукой — просто и эффективно.", Loader: qr },
    {bgColor: "#F7E8FF", title:"Удобно и на сайте,и в расширении",text:"Используйте наш сервис как на сайте, так и в расширении для браузера. Вся функциональность — там, где вам удобнее.", Loader: coin}
]
onMounted(() => {
gsap.registerPlugin(ScrollTrigger, ScrollToPlugin);
const cards = gsap.utils.toArray(".block__card_anim");
const tl = gsap.timeline();

cards.forEach((panel, index) => {
  let scale = 1;

  // If the current image is not the last one, adjust the scale based on its index  
  if (index !== cards.length - 1) {
    scale = 0.9 + 0.025 * index; // Create a slight scaling effect for images based on their index
  }

  gsap.to(panel, {
    scale: scale,
    transformOrigin: "top center",
    ease: "none",
    scrollTrigger: {
      trigger: panel,
      start: "top " + (70 + 40 * index),
      end: "bottom +=650px",
      endTrigger: ".end",
      pin: true, // Pin the current panel/image in place while it is being triggered
      pinSpacing: false, // Disable additional spacing around pinned elements
      scrub: true, 
      markers: true,
    }
  })
})

// gsap.timeline({
//   scrollTrigger: {
//     trigger: endBlock.value, // Родительский блок
//     start: "top top", // Начало эффекта
//     end: "bottom", // Длина анимации
//     pin: true, // Фиксируем родительский блок
//     scrub: 1, // Связь анимации с прокруткой
//     markers: true, // Показываем маркеры (для отладки)
//   },
// })

// cards.forEach((card, index) => {
//   tl.set(card, {
//     y: "300%",
//   })
//   // tl.to(card, {
//   //  scrollTrigger: {
//   //   trigger: endBlock.value,
//   //   start: "top top",
//   //   pin:true,
//   //   markers: true,
//   //  },
//   //  y: "100%",
//   //   duration: 1,
//   // })

//   })
})
</script>

<style lang="scss" scoped>
@use "/src/assets/scss/includes/media-queries";

.benefits {
  overflow: hidden;
  width: 100%;

  @include media-queries.media-large {
    margin-bottom: 120px;
  }

  @include media-queries.media-medium {
    margin-top: -100px;
    margin-bottom: 80px;
  }

  @include media-queries.media-small {
    margin-top: -30px;
    margin-bottom: 64px;
  }
}

.title {
  @include media-queries.media-large {
    margin-bottom: 60px;
  }
  @include media-queries.media-medium {
    margin-bottom: 20px;
  }

  @include media-queries.media-small {
    margin-bottom: 20px;
  }
}

.block {
  display: flex;
  flex-direction: column;
  overflow: hidden;

  @include media-queries.media-large {
    & div:not(:first-child) {
      margin-top: -120px;
    }
  }

  @include media-queries.media-medium {
    gap: 20px;
  }

  @include media-queries.media-small {
    gap: 20px;
  }
}
</style>
