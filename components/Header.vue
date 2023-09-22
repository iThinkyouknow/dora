<template>
    <header class="h-16 px-16 flex items-center justify-between sticky top-0 w-screen bg-white">
        <div class="left flex">
            <a href="/">
                <img class="logo" src="https://dorahacks.io/_nuxt/d271a54d.svg" alt="DoraHacks">
            </a>
            <ul class="flex gap-5 font-semibold ml-11 text-lg">
                <li>
                    <div>
                        <img src="https://dorahacks.io/_nuxt/018dbd2e.svg" alt="Other Sites">
                    </div>
                </li>
                <li v-for="link in headerLinks" :key="link.title" class="cursor-pointer">
                    {{ link.title }}
                </li>
            </ul>
        </div>
        <div class="right flex justify-between items-center gap-4">
            <div class="cursor-pointer">🔍</div>
            <button class="rounded-md border border-orange-500 py-1 px-3 text-orange-500 text-sm">Log in / Sign up</button>
            <div class="cursor-pointer">English</div>
        </div>
    </header>
</template>
<script lang="ts" setup>
const headerLinks = [
    {
        title: 'BUIDLs',
        link: ''
    },
    {
        title: 'Grants',
        link: ''
    },
    {
        title: 'Bounties',
        link: ''
    },
    {
        title: 'Hackathons',
        link: ''
    },
    {
        title: 'Ideas',
        link: ''
    },
    {
        title: 'Live',
        link: ''
    },
]
</script>