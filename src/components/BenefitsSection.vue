<template>
    <div class="container benefits__container">
        <H2Title class="title">Наши преимущества</H2Title>
        <div>
            <BenefitsCard bgColor="#E5F2FF" imgSRC="./src/assets/img/Ill01.png">
                <template v-slot:title>
                    QR-коды<br /> с креативным подходом
                </template>
                <template v-slot:text>
                    Создавайте оригинальные QR-коды, которые выделяются и подчеркивают ваш стиль. Простота, удобство и
                    креативность в одном решении.
                </template>
            </BenefitsCard>
        </div>
    </div>
</template>

<script lang="js" setup>
import BenefitsCard from "./BenefitsCard.vue";
import H2Title from "./H2Title.vue";
</script>

<style lang="scss" scoped>
@use "/src/assets/scss/includes/media-queries";

.benefits__container {
    @include media-queries.media-large {
        margin-top: -50px;
    }

    @include media-queries.media-medium {
        margin-top: -135px;
    }

    @include media-queries.media-small {
        margin-top: -50px;
    }
}

.title {
    margin-bottom: 20px;

    @include media-queries.media-large {
        margin-bottom: 60px;
    }
}
</style>