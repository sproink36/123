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
import { nextTick, onMounted, ref, watch } from "vue";
import gsap from "gsap";
import { ScrollToPlugin } from "gsap/all";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import "toolcool-range-slider";
import Swiper from "swiper";
import { Navigation, Pagination } from "swiper/modules";
// import Swiper and modules styles
import "swiper/css";
import "swiper/css/navigation";
import "swiper/css/pagination";
import Header from "../components/Header.vue";
import H1Title from "../components/H1Title.vue";
import BrowserButton from "../components/BrowserButton.vue";
import H2Title from "../components/H2Title.vue";
import DecisionBlock from "../components/DecisionBlock.vue";
import BenefitsSection from "../components/BenefitsSection.vue";
import PlatformsSection from "../components/PlatformsSection.vue";
import FAQSection from "../components/FAQSection.vue";
import Footer from "../components/Footer.vue";
import QRCodeGeneratorSection from "../components/QRCodeGeneratorSection.vue";
import { useMedia } from "../hooks/useMedia";

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

gsap.registerPlugin(ScrollTrigger, ScrollToPlugin);
const qrGenerator = ref();
const main = ref();
const header = ref();

// function getElementPositionByHeight(className) {
//   const element = document.querySelector(className); // Находим элемент по классу

//   if (!element) {
//     console.error("Элемент с таким классом не найден");
//     return;
//   }

//   // Получаем позицию элемента относительно всего документа
//   const rect = element.getBoundingClientRect();
//   const position = rect.top + window.scrollY; // Положение относительно начала страницы

//   return position;
// }

// const isScrollingDown = ref(false); // Переменная для отслеживания прокрутки вниз
// const isScrollingUp = ref(false); // Переменная для отслеживания прокрутки вверх

let lastScrollY = 0; // Переменная для хранения предыдущей позиции прокрутки

const getElementPositionByHeight = (className) => {
  const element = document.querySelector(className);
  if (element) {
    return element.getBoundingClientRect().height; // Получаем высоту через getBoundingClientRect()
  }
  return 0; // Возвращаем 0, если элемент не найден
};

const handleScroll = () => {
  const currentScrollY = window.scrollY;

  if (currentScrollY > lastScrollY) {
    // Если прокрутка вниз
    gsap.to(".main__header", { y: "-100%", opacity: 0, duration: 0.7 });
    // isScrollingDown.value = true;
    // isScrollingUp.value = false;
  } else {
    gsap.to(".main__header", { y: 0, opacity: 1, duration: 0.7 });
    // isScrollingDown.value = false;
    // isScrollingUp.value = true;
  }
  // console.log(isScrollingDown.value, isScrollingUp.value);

  // Обновляем последнюю позицию прокрутки
  lastScrollY = currentScrollY;
};

const childComponent = ref(null);
onMounted(() => {
  const mediaLarge = useMedia("(min-width: 1520px)");
  const mediaMedium = useMedia("(min-width: 768px) and (max-width: 1519px)");
  const mediaSmall = useMedia("(max-width: 768px)");
  
  const updateMainPadding = () => {
    let mainPaddingTop = 0;

    if (mediaLarge.value) {
      mainPaddingTop = 100;
    } else if (mediaMedium.value) {
      mainPaddingTop = 60;
    } else if (mediaSmall.value) {
      mainPaddingTop = 40;
    }

    const headerHeight = getElementPositionByHeight(".main__header");
    main.value.style.paddingTop = `calc(${headerHeight}px + ${mainPaddingTop}px)`;
  };

  // Update padding when window resizes
  watch([mediaLarge, mediaMedium, mediaSmall], updateMainPadding);

  // Initial setup
  updateMainPadding();

  window.addEventListener("scroll", handleScroll);

  ScrollTrigger.matchMedia({
    "(min-width: 1520px)": () => {
      ".section_anim_QRCodeGeneratorSection",
        ScrollTrigger.create({
          trigger: ".main",
          start: "top+=1 top", // Анимация активируется в указанной позиции
          once: true, // Анимация срабатывает только один раз
          markers: true,
          onEnter: () => {
            if (window.scrollY < 100) {
              gsap.to(window, {
                scrollTo: {
                  y: ".section_anim_QRCodeGeneratorSection",
                  autoKill: false,
                },
                duration: 1.8,
              });
            }
            // Вызываем метод дочернего компонента
            childComponent.value?.animateSection();
            // gsap.to(".section_anim_QRCodeGeneratorSection", {minHeight: "100vh"}, "<");
            // gsap.to(".main__header", { y: 60, duration: 0.7});
          },
        });
    },
  });
});
</script>

<template>
  <div class="main" ref="main">
    <Header class="main__header" ref="main__header" />
    <div class="container container_1 main__container">
      <H1Title class="title container_1__title-h1">
        Сервис генерации<br />
        куаркодов
      </H1Title>
      <p class="sub-title">
        Бесплатный сервис для создания QR-кодов<br />с расширенными
        возможностями аналитики
      </p>
      <BrowserButton class="main__btn main__btn_anim"
        >Скачать для браузера</BrowserButton
      >
    </div>
    <div
      class="container_1 section_anim section_anim_QRCodeGeneratorSection"
      ref="qrGenerator"
    >
      <QRCodeGeneratorSection ref="childComponent" />
    </div>
    <div class="section_anim_DecisionBlock">
      <DecisionBlock />
    </div>
    <div class="section_anim_BenefitsSection">
      <BenefitsSection />
    </div>
    <div class="section_anim section_anim_PlatformsSection">
      <PlatformsSection />
    </div>
    <FAQSection />
    <Footer />
  </div>
</template>

<style lang="scss" scoped>
@use "/src/assets/scss/includes/media-queries";
.main {
  display: flex;
  flex-direction: column;
  align-items: center;

  & .main__container {
    padding-top: 0;
  } 

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

.main__header {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 1000;
}

.anim_cont {
  scroll-snap-type: y mandatory;
}

.section_anim_QRCodeGeneratorSection {
  @include media-queries.media-large {
    min-height: 100vh;
  }
}

.section_anim {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  scroll-snap-align: start;
}

.section_anim_BenefitsSection {
  min-height: 100vh;
  overflow: hidden;
}

.container_1 {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.title {
  @include media-queries.media-small {
    margin-bottom: 20px;
  }
}

.container_1__title-h1 {
  // opacity: 0;
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
