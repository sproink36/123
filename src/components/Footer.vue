<template>
  <div class="block">
    <div class="container block__container">
      <div class="main_block">
        <div class="block_1">
          <p class="text">
            Бесплатный сервис для создания QR-кодов с расширенными возможностями
            аналитики
          </p>
          <Button class="btn" borderColor="#18213C" bgColor="#20D647" textColor="#18213C">Скачать для браузера</Button>
          <Button class="btn" borderColor="#18213C" bgColor="#18213C" textColor="white">Сгенерировать куаркод</Button>
        </div>
        <div class="img_block">
          <img :src="Frame" alt="" />
        </div>
        <div class="block_2">
          <div class="links">
            <a href="#">Преимущества</a>
            <a href="#">Расширение/плагин</a>
            <a href="#">FAQ</a>
            <a href="#">Вход/регистрация</a>
          </div>
          <div class="links">
            <a href="#">ВКонтакте</a>
            <a href="#">Инстаграм</a>
          </div>
        </div>
      </div>
      <div class="footer">
        <a href="#">Политика конфиденциальности</a>
        <a href="#">support@qrcode.ru</a>
        <a href="#">©куаркод.инк 2024</a>
      </div>
    </div>
  </div>
</template>

<script setup lang="js">
import Button from "./Button.vue"
import Frame from "/src/assets/img/Frame 16.png"
</script>

<style lang="scss" scoped>
@use "/src/assets/scss/includes/media-queries";

.block {
  background-color: #f3f5f7;
  width: 100%;
  padding: 40px 0;

  @include media-queries.media-large {
    padding: 80px 0;
  }
}

.block__container {
  padding-top: 0;
}

.main_block {
  display: flex;

  margin-bottom: 26px;
  flex-direction: column;
  align-items: center;

  @include media-queries.media-large {
    flex-direction: row;
    justify-content: space-between;
  }
}

.block_1 {
  display: flex;
  flex-direction: column;
  width: 330px;
  order: 1;

  @include media-queries.media-medium {
    width: 100%;
    gap: 20px;
    margin-bottom: 50px;
  }

  @include media-queries.media-small {
    gap: 20px;
    margin-bottom: 40px;
  }

  & .text {
    margin-bottom: 40px;
    font-size: 18px;
    font-weight: 500;
    line-height: 24px;
    text-align: left;

    @include media-queries.media-medium {
      text-align: center;
      margin-bottom: 0;
    }

    @include media-queries.media-small {
      text-align: center;
      margin-bottom: 0;
    }
  }

  & .btn:not(:last-child) {
    margin-bottom: 0;

    @include media-queries.media-large {
      margin-bottom: 20px;
    }
  }
}

.img_block {
  order: 2;
  width: 334px;
  height: 334px;
  object-fit: cover;

  @include media-queries.media-medium {
    order: 3;
    margin-bottom: 40px;
  }

  @include media-queries.media-small {
    order: 3;
    margin-bottom: 40px;
  }

  &>img {
    width: 100%;
    height: 100%;
  }
}

.block_2 {
  order: 3;
  display: flex;
  gap: 60px;

  @include media-queries.media-medium {
    order: 2;
    width: 100%;
    justify-content: space-between;
    margin-bottom: 58px;
  }

  @include media-queries.media-small {
    gap: 70px;
    flex-direction: column;
    order: 2;
    margin-bottom: 40px;
  }

  & .links {
    display: flex;
    flex-direction: column;
    gap: 10px;

    @include media-queries.media-small {
      align-items: center;
      gap: 30px;
    }

    & a {
      font-size: 18px;
      line-height: 24px;
      font-weight: 500;
    }
  }
}

.footer {
  display: flex;
  align-items: center;
  gap: 77px;

  @include media-queries.media-small {
    flex-direction: column;
    gap: 20px;
    align-items: center;
  }

  & a {
    font-size: 18px;
    font-weight: 500;
    line-height: 24px;
    color: #26272a4d;
  }

  & a:first-child {
    margin-right: auto;

    @include media-queries.media-medium {
      margin-right: 0;
    }

    @include media-queries.media-small {
      margin-right: 0;
    }
  }

  @include media-queries.media-medium {
    justify-content: space-between;
    gap: 0;
  }
}
</style>
