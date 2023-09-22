<style>
.orange-gradient-text {
    background: linear-gradient(90.73deg, #fa8e51 -3.63%, #ffca40 12.25%, #ff832a 78.91%);
    -webkit-text-fill-color: transparent;
    text-fill-color: transparent;
    -webkit-background-clip: text;
    background-clip: text;
}
</style>
<template>
    <div>
        <h3 class="text-5xl font-semibold text-center"><span class="orange-gradient-text">DoraHacks’</span> 5 core functions
        </h3>
    </div>
    <div class="mt-12 w-full flex justify-center">
        <div class="w-5/6 flex gap-8 justify-center">
            <CoreSectionButton v-for="button in buttons" :key="button.text" :text="button.text" :link="button.link" />
        </div>
    </div>
</template>
<script lang="ts" setup>
const buttons = [
    {
        text: 'BUIDLs',
        link: '#buidl'
    },
    {
        text: 'Grant DAOs',
        link: '#grant-dao'
    },
    {
        text: 'Hackathons',
        link: '#hackathon'
    },
    {
        text: 'Bounties',
        link: '#bounty'
    },
    {
        text: 'Community Voting',
        link: '#community-voting'
    },
]
</script>