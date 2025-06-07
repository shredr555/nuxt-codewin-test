<script setup lang='ts'>
const {data: slidesRaw} = await useFetch('https://api.los-bio.ru/info/group/slide')
const {data: advantagesRaw} = await useFetch('https://api.los-bio.ru/info/group/advantage')
const {data: projects} = await useFetch('https://api.los-bio.ru/projects/')

function parseValueList(rawList: Ref<any[] | undefined>) {
    return computed(() => 
        rawList.value?.map(item => {
            const parsed = JSON.parse(item.value)
            return {
                id: item.id,
                ...parsed
            }
        }) || []
    )
}

const slides = parseValueList(slidesRaw)
const advantages = parseValueList(advantagesRaw)
</script>

<template lang="pug">
SliderBlock(:slides='slides')
AdvantagesBlock(:items='advantages')
ProjectsGrid(:projects='projects')
</template>