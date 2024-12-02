<template>
  <div class="benefits">
    <div class="container">
      <H2Title class="title">Наши преимущества</H2Title>
      <div class="block">
        <BenefitsCard
          v-for="item in data"
          :key="item.bgColor"
          :bgColor="item.bgColor"
          :title="item.title"
          :text="item.text"
          :imgSRC="item.imgSRC"
        />
      </div>
    </div>
  </div>
</template>

<script lang="js" setup>
import BenefitsCard from "./BenefitsCard.vue";
import H2Title from "./H2Title.vue";

const data =
[
    {bgColor: "#E5F2FF", title: "QR-коды с креативным подходом", text: "Создавайте оригинальные QR-коды, которые выделяются и подчеркивают ваш стиль. Простота, удобство и креативность в одном решении.", imgSRC: "../src/assets/img/Ill01.png"},
    {bgColor: "#FFF3DE",title:"Вся статистика— в одном месте", text: "Удобно собирайте и анализируйте данные о QR-кодах в одном месте. Все нужные метрики всегда под рукой.", imgSRC: "../src/assets/img/Ill02.png"},
    {bgColor:"#FBFFE3", title:"Ведите проектыбез лишних забот",text:"Управляйте проектами легко и без стресса. Все инструменты под рукой — просто и эффективно.", imgSRC: "../src/assets/img/Ill03.png"},
    {bgColor: "#F7E8FF", title:"Удобно и на сайте,и в расширении",text:"Используйте наш сервис как на сайте, так и в расширении для браузера. Вся функциональность — там, где вам удобнее.", imgSRC: "../src/assets/img/Ill04.png"}
]
</script>

<style lang="scss" scoped>
@use "/src/assets/scss/includes/media-queries";

.benefits {
  overflow: hidden;
  width: 100%;
  position: relative;
  
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
