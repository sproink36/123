<template>
  <div class="section">
    <div class="container section__container">
      <div class="block_1">
        <div class="tags">
          <ButtonTag title="URL-адрес" @select-tag="selectTag" :currentTag>
            <Link />
          </ButtonTag>
          <ButtonTag title="Текст" @select-tag="selectTag" :currentTag>
            <Text />
          </ButtonTag>
          <ButtonTag title="Сообщение" @select-tag="selectTag" :currentTag>
            <Message />
          </ButtonTag>
          <ButtonTag title="Электронная почта" @select-tag="selectTag" :currentTag>
            <Mail />
          </ButtonTag>
        </div>
        <input class="input_url" v-model="input" type="text" placeholder="URL ссылка на сайт" />
      </div>
      <div class="generator">
        <div class="canvas"></div>
        <Button class="btn" borderColor="#18213C" bgColor="#18213C" textColor="white">Сохранить куаркод</Button>
        <div class="selector_type">
          <div v-for="item in types" :key="item" class="btn_type" :class="{ active: currentType === item }"
            @click="currentType = item">{{ item }}</div>
        </div>
      </div>
      <div class="settings">
        <SettingsMenu title="Настройки цвета" :currentSetting @select-settings="selectSettings">
          <template v-slot:icon>
            <Pallet />
          </template>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Soluta
          dolore nemo maxime doloremque nihil deleniti distinctio cupiditate
          blanditiis, ut itaque dolores mollitia asperiores ab corrupti id
          similique ea exercitationem facilis?
        </SettingsMenu>
        <SettingsMenu title="Настройки дизайна" :currentSetting @select-settings="selectSettings">
          <template v-slot:icon>
            <Pero />
          </template>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Soluta
          dolore nemo maxime doloremque nihil deleniti distinctio cupiditate
          blanditiis, ut itaque dolores mollitia asperiores ab corrupti id
          similique ea exercitationem facilis?
        </SettingsMenu>
        <SettingsMenu title="Настройки рамки" :currentSetting @select-settings="selectSettings">
          <template v-slot:icon>
            <Square />
          </template>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Soluta
          dolore nemo maxime doloremque nihil deleniti distinctio cupiditate
          blanditiis, ut itaque dolores mollitia asperiores ab corrupti id
          similique ea exercitationem facilis?
        </SettingsMenu>
        <SettingsMenu title="Логотип" :currentSetting @select-settings="selectSettings">
          <template v-slot:icon>
            <Spin />
          </template>
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

const currentTag = ref("URL-адрес");
const currentSetting = ref(null);
const currentType = ref(null);
const input = ref("");
const types = [".png", ".jpg", ".svg", ".pdf"]
function selectSettings(setting) {
  if (currentSetting.value === setting) {
    currentSetting.value = null;
  } else {
    currentSetting.value = setting;
  }
}

function selectTag(title) {
  currentTag.value = title;
}
</script>

<style lang="scss" scoped>
@use "/src/assets/scss/includes/media-queries";

.section {
  background-color: #f3f5f7;
  min-width: 100%;
  margin-bottom: 20px;
  border-radius: 40px;

  @include media-queries.media-large {
    width: 1600px;

  }
}

.section__container {
  padding-top: 0;
  display: flex;
  flex-direction: column;
  align-items: center;

  .block_1,
  .settings,
  .generator {
    width: 100%;
    display: flex;
  }

  @include media-queries.media-large {
    gap: 40px;
    justify-content: space-between;
    align-items: flex-start;
    flex-direction: row;
    max-height: 642px;
    padding-top: 60px;
    padding-bottom: 60px;
  }

  @include media-queries.media-medium {
    padding-top: 40px;
    padding-bottom: 40px;
  }

  @include media-queries.media-small {
    padding-top: 20px;
    padding-bottom: 20px;
  }
}

.block_1 {
  flex-direction: column;
  gap: 32px;
  order: 1;

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

    @include media-queries.media-small {
      &::placeholder {
      font-size: 14px;
      line-height: 24px;
    }
    }
  }

  @include media-queries.media-medium {
    gap: 42px;
    margin-bottom: 60px;
  }

  @include media-queries.media-small {
    gap: 42px;
    margin-bottom: 40px;
  }
}

.generator {
  padding: 30px;
  flex-direction: column;
  gap: 20px;
  align-items: center;
  border: 2px solid #18213c;
  border-radius: 40px;
  order: 2;

  .canvas {
    width: 100%;
    height: 180px;

    display: flex;
    align-items: center;
    justify-content: center;
    padding: 30px 0;
    background-color: white;
    border-radius: 20px;

    @include media-queries.media-large {
      height: 280px;
    }
  }

  @include media-queries.media-medium {
    order: 3;
  }

  @include media-queries.media-small {
    gap: 0;
    order: 3;

    & .canvas {
      margin-bottom: 20px;
    }

    & .btn {
      margin-bottom: 10px;
    }
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
    grid-template-rows: 64px 64px;

    gap: 10px;
  }

  .btn_type {
    display: flex;
    align-items: center;
    justify-content: center;
    border: 2px solid #bfbfbf;
    font-size: 18px;
    font-weight: 500;
    line-height: 24px;
    color: #bfbfbf;
    border-radius: 20px;

    &.active {
      border-color: #18213c;
      color: #18213c;
    }

    @include media-queries.media-large {
      grid-template-rows: 84px 84px;
      font-size: 15px;
    }

    @include media-queries.media-small {
      font-size: 15px;
    }
  }
}

.settings {
  flex-direction: column;
  align-items: flex-start;
  gap: 10px;
  order: 3;

  @include media-queries.media-medium {
    order: 2;
    margin-bottom: 40px;
  }

  @include media-queries.media-small {
    order: 2;
    margin-bottom: 40px;
  }
}
</style>
