<template>
  <div class="button-container">
    <button
      class="animated-button"
      @mouseenter="fillWithWater"
      @mouseleave="resetFill"
      ref="button"
    >
      Hover Me
    </button>
  </div>
</template>

<script>
import { gsap } from "gsap";

export default {
  name: "WaterFillButton",
  methods: {
    fillWithWater() {
      const button = this.$refs.button;

      gsap.to(button, {
        "--water-fill-height": "0%", // Начинаем с полного заполнения
        duration: 1,
        ease: "power2.out",
      });
    },
    resetFill() {
      const button = this.$refs.button;

      gsap.to(button, {
        "--water-fill-height": "100%", // Возвращаем на исходное положение
        duration: 1,
        ease: "power2.out",
      });
    },
  },
};
</script>

<style scoped>
.animated-button {
  position: relative;
  display: inline-block;
  padding: 10px 20px;
  font-size: 16px;
  color: #fff;
  background: none;
  border: 2px solid #58a;
  border-radius: 5px;
  overflow: hidden;
  cursor: pointer;

  /* Переход для текста */
  transition: color 0.3s ease;

  /* Переменная для высоты заливки */
  --water-fill-height: 100%;
}

.animated-button::before {
  content: "";
  position: absolute;
  top: var(--water-fill-height); /* Управляем высотой */
  left: 0;
  width: 100%;
  height: 200%; /* Чтобы градиент выглядел плавно */
  background: linear-gradient(0deg, rgba(58, 123, 213, 1) 0%, rgba(135, 182, 255, 1) 100%);
  transition: top 0.3s ease-out;
  z-index: 0;
  pointer-events: none;
}

.animated-button:hover {
  color: #000; /* Изменение цвета текста */
}

.animated-button span {
  position: relative;
  z-index: 1;
}
</style>