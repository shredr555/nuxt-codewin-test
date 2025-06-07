<script setup lang='ts'>
defineProps({
    items: Array
})
</script>

<template lang='pug'>
section.advantages
    .container
        h2.advantages__title Наши преимущества
        .advantages__grid
            div.advantages__item(v-for='item in items' :key='item.id')
                .advantages__item__top
                    img(:src='item.icon', :alt='item.title')
                    h3 {{ item.title }}
                .advantages__item__bottom
                    p {{ item.description }}
</template>