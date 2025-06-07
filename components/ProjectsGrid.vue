<script setup lang='ts'>
defineProps({
    projects: Array
})

const link = 'https://api.los-bio.ru/projects/'
</script>

<template lang='pug'>
section.project
    .container
        h2.project__title Проекты
        .project__grid
            NuxtLink.project__card(v-for='project in projects' :key='project.id' :to='"/projects/" + project.slug')
                img(:src='"https://api.los-bio.ru/files/" + project.photos[0].catalog + "/" + project.photos[0].name')
                h4 {{ project.title }}
                p {{ project.short_description.blocks[0].data.text }}
                p #[span Тип работы: ] {{ project.works }}
                p #[span Заказчик: ] {{ project.customer }}
</template>