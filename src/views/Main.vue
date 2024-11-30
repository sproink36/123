<script setup>
import { Vue3Lottie } from "vue3-lottie";
import Kianu from "../animations/pc/kianu.json";
import Ded from "../animations/pc/ded.json";
import Fire from "../animations/pc/fire.json";
import Jdun from "../animations/pc/jdun.json";
import KianuMob from "../animations/mob/kianu.json";
import DedMob from "../animations/mob/ded.json";
import FireMob from "../animations/mob/fire.json";
import JdunMob from "../animations/mob/jdun.json";
import { onMounted, ref } from "vue";
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import "toolcool-range-slider";
import Swiper from "swiper";
import { Navigation, Pagination } from "swiper/modules";
// import Swiper and modules styles
import "swiper/css";
import "swiper/css/navigation";
import "swiper/css/pagination";
import Test from "../components/Test.vue";
import Header from "../components/Header.vue";
import H1Title from "../components/H1Title.vue";
import BrowserButton from "../components/BrowserButton.vue";
import H2Title from "../components/H2Title.vue";
import DecisionBlock from "../components/DecisionBlock.vue";
import BenefitsSection from "../components/BenefitsSection.vue";

// gsap.registerPlugin(ScrollTrigger);

// const data = ref({
//   animation: 1,
//   isMob: false,
// });

// const lotie1 = ref(null);

// let swiper;

// onMounted(() => {
//   const widthAnimation =
//     document.querySelector(".lottie-animation-container").offsetWidth * 3;
//   const tlChoose = gsap.timeline();

//   window.addEventListener("resize", () => {
//     if (window.innerWidth < 1080) {
//       data.value.isMob = true;
//     } else {
//       data.value.isMob = false;
//       lotie1.value.setDirection("reverse");
//       lotie1.value.playSegments([1, 50], true);
//     }
//   });

//   if (window.innerWidth < 1080) {
//     data.value.isMob = true;
//   } else {
//     data.value.isMob = false;
//   }

//   if (!data.value.isMob) {
//     tlChoose.to(".animation-wrap", {
//       scrollTrigger: {
//         trigger: ".animation-wrap",
//         start: `top top`,
//         end: `=${widthAnimation}`,
//         scrub: 1,
//         pin: true,
//         endTrigger: ".end",
//         snap: {
//           snapTo: "labels", // snap to the closest label in the timeline
//           duration: { min: 0.2, max: 3 }, // the snap animation should be at least 0.2 seconds, but no more than 3 seconds (determined by velocity)
//           delay: 0.2, // wait 0.2 seconds from the last scroll event before doing the snapping
//           ease: "power1.inOut", // the ease of the snap animation ("power3" by default)
//         },
//       },
//       left: `-${widthAnimation}px`,
//       stagger: 0.5,
//     });
//   }

//   swiper = new Swiper(".swiper", {
//     // Optional parameters
//     direction: "horizontal",
//     loop: false,

//     slidesPerView: 1,
//   });
// });
</script>

<template>
  <div class="main">
    <Header />
    <div class="container container_1">
      <H1Title>
        Сервис генерации<br />
        куаркодов
      </H1Title>
      <p class="sub-title">
        Бесплатный сервис для создания QR-кодов<br />с расширенными
        возможностями аналитики
      </p>
      <BrowserButton class="main__btn">Скачать для браузера</BrowserButton>
    </div>
    <!-- <iframe src="/qr-mech/index.html" width="100%"></iframe> -->
    <DecisionBlock />
    <BenefitsSection />
  </div>
</template>

<style lang="scss" scoped>
@use "/src/assets/scss/includes/media-queries";
.main {
  display: flex;
  flex-direction: column;
  align-items: center;
  
  & .main__btn {
    margin-bottom: 120px;

    @include media-queries.media-large {
      margin-bottom: 120px;
    }

    @include media-queries.media-medium {
      margin-bottom: 80px;
    }

    @include media-queries.media-small {
      margin-bottom: 60px;
    }
  }
}

.container_1 {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.sub-title {
  text-align: center;
  margin-bottom: 40px;
  line-height: 40px;
  font-size: 28px;

  @include media-queries.media-medium {
    line-height: 24px;
  }

  @include media-queries.media-small {
    line-height: 24px;
    margin-bottom: 44px;
    font-size: 14px;
  }
}
</style>
