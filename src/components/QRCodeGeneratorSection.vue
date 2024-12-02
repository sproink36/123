<template>
  <div class="section">
    <div class="container section__container">
      <div class="block_1">
        <div class="tags">
          <ButtonTag>
            <template v-slot:text>URL-адрес</template>
            <template v-slot:icon><Link /></template>
          </ButtonTag>
          <ButtonTag>
            <template v-slot:text>Текст</template>
            <template v-slot:icon><Text /></template>
          </ButtonTag>
          <ButtonTag>
            <template v-slot:text>Сообщение</template>
            <template v-slot:icon><Message /></template>
          </ButtonTag>
          <ButtonTag>
            <template v-slot:text>Электронная почта</template>
            <template v-slot:icon><Mail /></template>
          </ButtonTag>
        </div>
        <input class="input_url" type="text" placeholder="URL ссылка на сайт" />
      </div>
      <div class="generator">
        <div class="canvas"></div>
        <Button
          class="btn"
          borderColor="#18213C"
          bgColor="#18213C"
          textColor="white"
          >Сохранить куаркод</Button
        >
        <div class="selector_type">
          <div class="btn_type">.png</div>
          <div class="btn_type">.jpg</div>
          <div class="btn_type">svg</div>
          <div class="btn_type">.pdf</div>
        </div>
      </div>
      <div class="settings">
        <SettingsMenu>
          <template v-slot:title>Настройки цвета</template>
          <template v-slot:icon><Pallet /></template>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Soluta
          dolore nemo maxime doloremque nihil deleniti distinctio cupiditate
          blanditiis, ut itaque dolores mollitia asperiores ab corrupti id
          similique ea exercitationem facilis?
        </SettingsMenu>
        <SettingsMenu>
          <template v-slot:title>Настройки дизайна</template>
          <template v-slot:icon><Pero /></template>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Soluta
          dolore nemo maxime doloremque nihil deleniti distinctio cupiditate
          blanditiis, ut itaque dolores mollitia asperiores ab corrupti id
          similique ea exercitationem facilis?
        </SettingsMenu>
        <SettingsMenu>
          <template v-slot:title>Настройки рамки</template>
          <template v-slot:icon><Square /></template>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Soluta
          dolore nemo maxime doloremque nihil deleniti distinctio cupiditate
          blanditiis, ut itaque dolores mollitia asperiores ab corrupti id
          similique ea exercitationem facilis?
        </SettingsMenu>
        <SettingsMenu>
          <template v-slot:title>Логотип</template>
          <template v-slot:icon><Spin /></template>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Soluta
          dolore nemo maxime doloremque nihil deleniti distinctio cupiditate
          blanditiis, ut itaque dolores mollitia asperiores ab corrupti id
          similique ea exercitationem facilis?
        </SettingsMenu>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import ButtonTag from "./ButtonTag.vue";
import { Link, Mail, Pero, Square, Text, Spin } from "../assets/icons";
import Message from "../assets/icons/Message.vue";
import Button from "./Button.vue";
import SettingsMenu from "./SettingsMenu.vue";
import Pallet from "../assets/icons/Pallete.vue";
</script>

<style lang="scss" scoped>
@use "/src/assets/scss/includes/media-queries";

.section {
  background-color: #f3f5f7;
  min-width: 100%;

  @include media-queries.media-large {
    width: 1600px;
    border-radius: 40px;
    padding: 60px 0;
  }
}

.section__container {
  padding-top: 0;
  display: flex;
  .block_1,
  .settings,
  .generator {
    width: 100%;
    display: flex;
  }
  @include media-queries.media-large {
    gap: 40px;
    justify-content: space-between;
  }
}

.block_1 {
  flex-direction: column;
  gap: 32px;

  .tags {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  .input_url {
    background-color: transparent;
    height: 40px;
    &::placeholder {
      font-size: 32px;
      line-height: 40px;
    }
  }
}

.generator {
  padding: 30px;
  flex-direction: column;
  gap: 20px;
  align-items: center;
  border: 2px solid #18213c;
  border-radius: 40px;

  .canvas {
    width: 100%;
    height: 280px;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 30px 0;
    background-color: white;
    border-radius: 20px;
  }

  & .btn {
    width: 100%;
  }

  .selector_type {
    width: 100%;
    display: grid;
    grid-auto-columns: 1fr;
    grid-auto-rows: 1fr;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: 84px 84px;
    gap: 10px;
  }

  .btn_type {
    display: flex;
    align-items: center;
    justify-content: center;
    border: 2px solid #a0a0a0;
    font-size: 18px;
    font-weight: 500;
    line-height: 24px;
    color: #a0a0a0;
    border-radius: 20px;
  }
}

.settings {
  flex-direction: column;
  align-items: flex-start;
  gap: 10px;
}
</style>
