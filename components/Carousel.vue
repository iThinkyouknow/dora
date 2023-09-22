<style scoped>
swiper-container {
    width: 100%;
    height: 100%;
}

swiper-slide {
    text-align: center;
    font-size: 18px;
    background: #fff;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 25%;
    height: 100%;
}

swiper-slide img {
    display: block;
    width: 100%;
    height: 100%;
    object-fit: cover;
}

swiper-container::part(button-prev),
swiper-container::part(button-next) {
    @apply text-white font-bold border border-solid border-white rounded-full w-[10px] h-[10px] p-2 mt-0
}
</style>
<template>
    <swiper-container space-between="30" slides-per-view="auto" :navigation="true" autoplay-delay="2500">
        <swiper-slide v-for="slide in slides" :key="slide.img">
            <img :src="slide.img" alt="banner" class="rounded rounded-2xl">
        </swiper-slide>
    </swiper-container>
</template>
<script setup lang="ts">
import { register } from 'swiper/element/bundle';
register();

const slides = [
    {
        img: 'https://cdn.dorahacks.io/static/files/18a8efabac827d53a288c3f4338bd169.jpg@256h.webp'
    },
    {
        img: 'https://cdn.dorahacks.io/static/files/189c0a756e8737d3d7301ba4c6ebd8bf.jpg@256h.webp'
    },
    {
        img: 'https://cdn.dorahacks.io/static/files/1886d7d77099f75d6c0902b4f9bb5618.jpg@256h.webp'
    },
    {
        img: 'https://cdn.dorahacks.io/static/files/189f474444dfca7aaf75a674f45964c2.png@256h.webp'
    },
    {
        img: 'https://cdn.dorahacks.io/static/files/18a2b73da295bd773085f6b44a0994e2.jpg@256h.webp'
    },
    {
        img: 'https://cdn.dorahacks.io/static/files/18a6afa30dcf6084a5e059a4affa5cc2.jpg@256h.webp'
    },
    {
        img: 'https://cdn.dorahacks.io/static/files/18a03b219a1960520c67c7d4d0aaf405.png@256h.webp'
    },
    {
        img: 'https://cdn.dorahacks.io/static/files/189062074873cf484b4c8054abe8576b.jpg@256h.webp'
    }
]


</script>