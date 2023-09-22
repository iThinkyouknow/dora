<template>
    <a :href="link">
        <button
            class="rounded-3xl shadow-xl text-xl border-transparent border  font-semibold w-[200px] h-[100px] hover:text-orange-500 hover:border ease-out	duration-300 transition hover:border-orange-500 hover:shadow-sm">
            {{ text }}
        </button>
    </a>
</template>
<script setup lang="ts">
const props = defineProps({
    text: String,
    link: String
})
</script>