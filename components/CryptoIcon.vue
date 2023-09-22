<template>
    <div class="border border-gray-200 rounded-xl absolute p-2 bg-white transition-transform ease-out duration-700"
        :class="[{ 'translate-y-40': !logoIsIntersecting }]" :style="style">
        <img :width="imgSize" :height="imgSize" :src="imgSrc" :alt="alt">
    </div>
</template>
<script lang="ts" setup>
const props = defineProps({
    imgSrc: String,
    alt: String,
    imgSize: Number,
    logoIsIntersecting: Boolean,
    order: Number,
    top: Number,
    left: Number,
    bottom: Number
})

const style = computed(() => {
    const topOrBottom = props.bottom ? `bottom: ${props.bottom}px` : `top: ${props.top}px`
    return `${topOrBottom}; left: ${props.left}px; width: ${props.imgSize}px; height: ${props.imgSize}px; transition-delay: ${(props.order ?? 0) * 50}ms`
})
</script>