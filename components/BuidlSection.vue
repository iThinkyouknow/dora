<style>
.buidl-details-container:hover .buidl-img {
    @apply -translate-x-2
}

.buidl-details-container:hover .buidl-details {
    @apply -translate-x-1
}

.buidl-details-container:hover .buidl-track {
    @apply translate-x-1
}
</style>
<template>
    <div class="flex gap-32" ref="buidlSectionRef">
        <div class="left border border-orange-500/20 rounded-lg w-7/12 p-8">
            <div class="flex gap-4">
                <a :href="banner.link" v-for="banner in banners" :key="banner.link">
                    <button class="rounded rounded-lg overflow-hidden">
                        <img :src="banner.src" alt="banner">
                    </button>
                </a>
            </div>
            <div class="mt-4">
                <div class="flex justify-between gap-2 py-2">
                    <div class="w-2/3 text-gray-300">
                        BUIDL Name
                    </div>
                    <div class="w-1/3 text-gray-300">
                        Track
                    </div>
                </div>
                <a v-for="(buidlName, i) in buidlNames" :key="buidlName.link" :href="buidlName.link"
                    class="flex py-2 gap-2 justify-between buidl-details-container ease-out duration-700 transition"
                    :class="{ 'opacity-0': !show, '-translate-x-8': !show }" :style="`transition-delay: ${i * 100}ms`">
                    <div class="w-2/3 flex gap-2 items-center">
                        <img :src="buidlName.src" alt="img" width="64" class="buidl-img transition-transform ease-in-out ">
                        <div class="flex flex-col overflow-hidden buidl-details transition-transform ease-in-out ">
                            <h5 class="text-lg">{{ buidlName.title }}</h5>
                            <p class="text-xs text-gray-400 truncate ">{{ buidlName.subtitle }}</p>
                        </div>
                    </div>
                    <div class="w-1/3 flex-1 flex gap-2 items-center buidl-track transition-transform ease-in-out ">
                        <span v-for="track in buidlName.tracks" :key="track"
                            class="bg-orange-300/20 text-orange-400 text-xs p-1 rounded">{{ track }}</span>
                    </div>
                </a>

            </div>
        </div>
        <div class="right flex flex-col gap-4 w-5/12 transition duration-700 ease-out"
            :class="{ 'translate-y-8': !show, 'opacity-0': !show }">
            <img src="data:image/jpeg;base64,iVBORw0KGgoAAAANSUhEUgAAANYAAADWCAYAAACt43wuAAABZ2lDQ1BEaXNwbGF5IFAzAAAokXXQsWtTcQDE8c9rlUKsg5ihQ4c3iUPUkgp2cWgrFEUwVIWkTq+vSVpI4o+XiFTcxFUK/gdWcBYcLCIVXBwcBNFBRDenTgouGp5DImkRb7njyw3HMTaVhNA6hHanly0vLcTV2ko88U0kApK0G+Yrlcvw1w/q58dB9/2pJITWXn/7wdz9pdftZy+v3Pk0debf/gEV1urdFL8xk4asR1RC5XYv9IjuophVaytEWyg2B/kxiquD/BzF7NryItFbxOl6ska0h9LqPt7cl9utW+lwQ4TJeuf6VRQx7YINXUFLYlOsYvY//bOYtuimYFNmQ9O6nti8IGipi13UkTqtJFY2o6xcra3Ew/8+DP8rjdi9r5zfzfP8xYhd2uXpOQo7I3ZyjmNHeLMTkiwB4xhrNPj+hKM1jr+jcKPbmC0P1k8ucPhLnv84wcRD+lt5/utRnve3Gf/Mq84fFylqvMNVpzcAAAAJcEhZcwAAJ18AACdfAR2GumoAAAZZaVRYdFhNTDpjb20uYWRvYmUueG1wAAAAAAA8P3hwYWNrZXQgYmVnaW49Iu+7vyIgaWQ9Ilc1TTBNcENlaGlIenJlU3pOVGN6a2M5ZCI/PiA8eDp4bXBtZXRhIHhtbG5zOng9ImFkb2JlOm5zOm1ldGEvIiB4OnhtcHRrPSJBZG9iZSBYTVAgQ29yZSA2LjAtYzAwNiA3OS5kYWJhY2JiLCAyMDIxLzA0LzE0LTAwOjM5OjQ0ICAgICAgICAiPiA8cmRmOlJERiB4bWxuczpyZGY9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkvMDIvMjItcmRmLXN5bnRheC1ucyMiPiA8cmRmOkRlc2NyaXB0aW9uIHJkZjphYm91dD0iIiB4bWxuczp4bXA9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC8iIHhtbG5zOmRjPSJodHRwOi8vcHVybC5vcmcvZGMvZWxlbWVudHMvMS4xLyIgeG1sbnM6cGhvdG9zaG9wPSJodHRwOi8vbnMuYWRvYmUuY29tL3Bob3Rvc2hvcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RFdnQ9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZUV2ZW50IyIgeG1wOkNyZWF0b3JUb29sPSJBZG9iZSBQaG90b3Nob3AgMjIuNCAoTWFjaW50b3NoKSIgeG1wOkNyZWF0ZURhdGU9IjIwMjMtMDMtMjJUMTQ6MjQ6MjcrMDg6MDAiIHhtcDpNb2RpZnlEYXRlPSIyMDIzLTAzLTIyVDE0OjM5OjA5KzA4OjAwIiB4bXA6TWV0YWRhdGFEYXRlPSIyMDIzLTAzLTIyVDE0OjM5OjA5KzA4OjAwIiBkYzpmb3JtYXQ9ImltYWdlL3BuZyIgcGhvdG9zaG9wOkNvbG9yTW9kZT0iMyIgcGhvdG9zaG9wOklDQ1Byb2ZpbGU9IkRpc3BsYXkgUDMiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6NWJkYTE0ZDAtZDUxYy00YmNjLTllNDEtYjdhZjVhYTU1ODc3IiB4bXBNTTpEb2N1bWVudElEPSJhZG9iZTpkb2NpZDpwaG90b3Nob3A6YjY4YzNlYjYtZjAxYi0yODQxLWE4YWItNjNiYmE1MzY0Y2VkIiB4bXBNTTpPcmlnaW5hbERvY3VtZW50SUQ9InhtcC5kaWQ6MWY1NTNlMzItZjJiMy00MDJlLTljMTgtNDMzMGNkNzlmYjYxIj4gPHhtcE1NOkhpc3Rvcnk+IDxyZGY6U2VxPiA8cmRmOmxpIHN0RXZ0OmFjdGlvbj0iY3JlYXRlZCIgc3RFdnQ6aW5zdGFuY2VJRD0ieG1wLmlpZDoxZjU1M2UzMi1mMmIzLTQwMmUtOWMxOC00MzMwY2Q3OWZiNjEiIHN0RXZ0OndoZW49IjIwMjMtMDMtMjJUMTQ6MjQ6MjcrMDg6MDAiIHN0RXZ0OnNvZnR3YXJlQWdlbnQ9IkFkb2JlIFBob3Rvc2hvcCAyMi40IChNYWNpbnRvc2gpIi8+IDxyZGY6bGkgc3RFdnQ6YWN0aW9uPSJjb252ZXJ0ZWQiIHN0RXZ0OnBhcmFtZXRlcnM9ImZyb20gYXBwbGljYXRpb24vdm5kLmFkb2JlLnBob3Rvc2hvcCB0byBpbWFnZS9wbmciLz4gPHJkZjpsaSBzdEV2dDphY3Rpb249InNhdmVkIiBzdEV2dDppbnN0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"
                alt="planet" height="146" width="146">
            <h3 class="text-4xl font-semibold">Top BUIDLs on DoraHacks</h3>
            <p class="text-gray-300 text-xl">
                Explore the multiverse of DoraHacks builders, hackers, and developers. Build future technology for the
                present and connect with each other.
            </p>
            <div class="flex gap-4">
                <div class="w-7/12">
                    <ButtonPrimary>
                        Submit BUIDL
                    </ButtonPrimary>
                </div>
                <ButtonGhost class="w-7/12">
                    Create BUIDL Collection
                </ButtonGhost>
            </div>
            <div class="flex flex-col gap-4">
                <ButtonArrow>View all BUIDLs</ButtonArrow>
                <ButtonArrow>BUIDL Guides</ButtonArrow>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
const banners = [
    {
        src: 'https://cdn.dorahacks.io/static/files/189ba3bbddb0ddab034a94a4c2bb6a3c.jpg@256h.webp',
        link: 'https://dorahacks.io/buidl-collection/611'
    },
    {
        src: 'https://cdn.dorahacks.io/static/files/189fea5ea3471aa63b18a1e4e0188adb.jpg@256h.webp',
        link: 'https://dorahacks.io/buidl-collection/648'
    },
    {
        src: 'https://cdn.dorahacks.io/static/files/189fea6c4d08c881ec60c2148dc91896.jpg@256h.webp',
        link: 'https://dorahacks.io/buidl-collection/649'
    }
]

const buidlNames = [
    {
        src: 'https://cdn.dorahacks.io/static/files/18ab85b3da067bee82dcda84fd9a4578.png@128h.webp',
        link: 'https://dorahacks.io/buidl/7414',
        title: 'ShadStaker',
        subtitle: 'ShadStaker is a decentralized application...',
        tracks: [
            'Secret Network',
            'Defi',
        ]
    },
    {
        src: 'https://cdn.dorahacks.io/static/files/18ab6a5a3886b0a8c9642304a1eacd0d.png@128h.webp',
        link: 'https://dorahacks.io/buidl/7410',
        title: 'Vladiators by Gnogen',
        subtitle: 'A Web3 native studio that specializes in creating digital collectibles, empowering IP expansion through exciting new technologies, within an ecosystem powered by our novel mining token built on proof of stake Multivserx (EGLD).',
        tracks: [
            'NFT',
            'GameFi',
        ]
    },
    {
        src: 'https://cdn.dorahacks.io/static/files/18ab5c29a28eeb772e019014f6d88ec7.png@128h.webp',
        link: 'https://dorahacks.io/buidl/7409',
        title: 'Planet Hares',
        subtitle: `Planet Hares is a metaverse ecosystem platform that empowers Web3 projects based on blockchain technology and entertainment culture.We have the following two products:`,
        tracks: [
            'Ethereum',
            'BNB Chain',
        ]
    },
    {
        src: 'https://cdn.dorahacks.io/static/files/18ab266f3aefb6646ea24c14d86bb61a.png@128h.webp',
        link: 'https://dorahacks.io/buidl/7407',
        title: 'Materia Prime',
        subtitle: 'Materia Prima is a Role Play Game set within the mystical world of Alka Sowa. As a player you can master the arts of alchemy to craft powerful items and create life in form of homunculi. Forge mighty alliances within the alchemist guild and fight against your opponents in PvE and PvP battles. In Materia Prima, players possess genuine ownership of their digital assets.',
        tracks: [
            'NFT',
            'GameFi',
        ]
    },
    {
        src: 'https://cdn.dorahacks.io/static/files/18ab0b64f260327498f1ba34993889b8.png@128h.webp',
        link: 'https://dorahacks.io/buidl/7405',
        title: 'NeoPay',
        subtitle: 'Updating...',
        tracks: [
            'DAO/Community',
            'Defi',
        ]
    },
];

const buidlSectionRef = ref();
const show = ref(false);

onMounted(() => {

    const observer = new IntersectionObserver(
        (entries) => {
            entries.forEach((entry) => {
                if (entry.isIntersecting) {
                    show.value = true;
                }
            });
        },
        {
            threshold: 0.5,
        }
    );

    observer.observe(buidlSectionRef.value)
})
</script>