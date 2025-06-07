<script setup lang='ts'>
import { useRoute } from '#imports'
import { ref } from 'vue';
import { Swiper, SwiperSlide } from 'swiper/vue';

import 'swiper/css';
import 'swiper/css/free-mode';
import 'swiper/css/navigation';
import 'swiper/css/thumbs';

import { FreeMode, Navigation, Thumbs } from 'swiper/modules';

const thumbsSwiper = ref(null)
const setThumbsSwiper = (swiper) => {
    thumbsSwiper.value = swiper
}
const modules = [FreeMode, Navigation, Thumbs]

const route = useRoute()
const slug = route.params.slug
const {data: project} = await useFetch(`https://api.los-bio.ru/projects/${slug}`)
</script>

<template lang='pug'>
.container
    .project__link
        NuxtLink(to='/') Главная
        .dot
        NuxtLink(to='/') Проекты
        .dot
        p {{ project.title }}
    .project__information
        .project__description
            h1 {{ project.title }}
            p {{ project.short_description.blocks[0].data.text }}
            div(v-for='(block) in project.description.blocks' :key='block.id')
                h2(v-if='block.type === "header"') {{ block.data.text }}
                p(v-if='block.type === "paragraph"') {{ block.data.text }}
                ul(v-if='block.type === "list"')
                    li(v-for='(item, i) in block.data.items' :key='i') {{ item }}
        .project__img
            swiper(
                :style="{ '--swiper-navigation-color': '#fff', '--swiper-pagination-color': '#fff' }"
                :loop="true"
                :spaceBetween="10"
                :navigation="true"
                :thumbs="{ swiper: thumbsSwiper }"
                :modules="modules"
                class="main-swiper"
            )
                swiper-slide(v-for='(photo, i) in project?.photos' :key='i')
                    img(:src='"https://api.los-bio.ru/files/" + photo.catalog + "/" + photo.name')
            swiper(
                @swiper="setThumbsSwiper"
                :loop="true"
                :spaceBetween="10"
                :slidesPerView="4"
                :freeMode="true"
                :watchSlidesProgress="true"
                :modules="modules"
                class="thumbs-swiper"
            )
                swiper-slide(v-for='(photo, i) in project?.photos' :key='`thumb-${i}`')
                    img(:src='"https://api.los-bio.ru/files/" + photo.catalog + "/" + photo.name')

</template>