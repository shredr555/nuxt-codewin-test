<script setup lang="ts">
import { Swiper, SwiperSlide } from 'swiper/vue'
import 'swiper/css'
import 'swiper/css/pagination'
import { Pagination } from 'swiper/modules'

defineProps({
    slides: Array
})

const modules = [Pagination]
</script>

<template lang='pug'>
section.slider
    .container(v-if='slides.length')
        swiper(
            :slidesPerView='1'
            :modules='modules'
            :loop='true'
            :autoplay='{ delay: 2500, disableOnInteraction: false, }'
            :pagination='{ dynamicBullets: true, }'
        )
            swiper-slide(v-for='slide in slides' :key='slide.id')
                .slider__content
                    .slider__text
                        h1 {{ slide.title }}
                        p {{ slide.description }}
                        a.slider__text-btn Перейти в каталог
                    .slider__img
                        img(:src='"https://api.los-bio.ru/files/" + slide.image[0].catalog + "/" + slide.image[0].name')
    div(v-else)
        p Загруа...
</template>