<style scoped>
.gradient-bg {
    background-image: linear-gradient(150deg, #faf3fe, #fff 16%, #fff 84%, #fff7f3)
}

.map-bg {
    background: url('https://dorahacks.io/_nuxt/49068c22.jpg')
}

.green-purple-text {
    background: linear-gradient(100deg, #7f4ec7 11.46%, #5594f1 42.58%, #58de98 50%, #5594f1 57.42%, #7f4ec7 88.54%) 100%/200% 100%;
    -webkit-background-clip: text;
    color: transparent;
}

.animate-green-purple-text {
    animation: background-shift 6s ease-in-out 0s infinite forwards;
}

@keyframes background-shift {
    0% {
        background-position: 0%;
    }

    30% {
        background-position: -10%;
    }
}
</style>
<template>
    <div class="flex flex-col items-center">
        <div class="rounded rounded-xl box-shadow gradient-bg w-5/6 p-8 z-10">
            <div class="flex gap-4 justify-between w-full" ref="elRef">
                <EcosystemValues text-color="green" title="Funded" :value="29.33" prefix="$" suffix="M" :order="1"
                    class="min-w-[158px]" :is-intersecting="ecoIsIntersecting">
                </EcosystemValues>
                <hr class="bg-gray-200 h-10 w-0.5 mx-4 self-center" />
                <EcosystemValues text-color="green" title="Community Contributions" :value="8.88" prefix="$" suffix="M"
                    :order="2" class="min-w-[236px]" :is-intersecting="ecoIsIntersecting">
                </EcosystemValues>
                <hr class="bg-gray-200 h-10 w-0.5 mx-4 self-center" />
                <EcosystemValues text-color="orange" title="BUIDLs" :value="7232" prefix="" suffix="" :order="3"
                    class="min-w-[100px]" :is-intersecting="ecoIsIntersecting">
                </EcosystemValues>
                <hr class="bg-gray-200 h-10 w-0.5 mx-4 self-center" />
                <EcosystemValues text-color="orange" title="Active Builders" :value="99363" prefix="" suffix="" :order="4"
                    class="min-w-[138px]" :is-intersecting="ecoIsIntersecting">
                </EcosystemValues>
            </div>

        </div>
        <div class="h-52 map-bg w-full -mt-20 flex justify-end mb-20">
            <div class="w-11/12 pt-24 flex justify-between gap-2 overflow-y-hidden">
                <div class="left flex-1">
                    <div class="mt-4">
                        <h2 class="text-2xl font-semibold">Build with the best ecosystems </h2>
                        <h2 class="text-2xl font-semibold">on <span
                                class="green-purple-text animate-green-purple-text">DoraHacks</span></h2>
                    </div>
                </div>
                <div class="right relative flex-1 " ref="logoRef">
                    <CryptoIcon v-for="(icon, i) in cryptoIcons" :key="icon.imgSrc" :logoIsIntersecting="logoIsIntersecting"
                        :imgSrc="icon.imgSrc" :alt="icon.alt" :imgSize="icon.imgSize" :top="icon.top" :bottom="icon.bottom"
                        :left="icon.left" :order="i" />
                </div>
            </div>
        </div>
    </div>
</template>
<script setup lang="ts">
const elRef = ref();
const logoRef = ref();
const ecoIsIntersecting = ref(false);
const logoIsIntersecting = ref(false);
const cryptoIcons = [
    {
        imgSrc: 'https://dorahacks.io/_nuxt/b1cefbd7.svg',
        alt: 'eth',
        imgSize: 64,
        top: 24,
        left: 0
    },
    {
        imgSrc: 'data:image/png;base64,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',
        alt: '',
        imgSize: 64,
        top: 48,
        left: 80
    },
    {
        imgSrc: 'https://dorahacks.io/_nuxt/d8f74907.svg',
        alt: '',
        imgSize: 64,
        top: 16,
        left: 160
    },
    {
        imgSrc: 'https://dorahacks.io/_nuxt/a7a03cd4.svg',
        alt: '',
        imgSize: 56,
        top: -8,
        left: 246
    },
    {
        imgSrc: 'https://dorahacks.io/_nuxt/198992be.svg',
        alt: '',
        imgSize: 64,
        bottom: -8,
        left: 254
    },
    {
        imgSrc: 'data:image/png;base64,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',
        alt: '',
        imgSize: 64,
        top: 20,
        left: 338
    },
    {
        imgSrc: 'https://dorahacks.io/_nuxt/4b8b7e8c.svg',
        alt: '',
        imgSize: 64,
        bottom: -8,
        left: 414
    },
    {
        imgSrc: 'https://dorahacks.io/_nuxt/133b503b.svg',
        alt: 'Solana',
        imgSize: 60,
        top: -16,
        left: 470
    },
]
onMounted(() => {

    const observer = new IntersectionObserver(
        (entries) => {
            entries.forEach((entry) => {
                if (entry.isIntersecting) {
                    ecoIsIntersecting.value = true;
                }
            });
        },
        {
            threshold: 0.5,
        }
    );

    observer.observe(elRef.value)

    const logoObserver = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            logoIsIntersecting.value = entry.isIntersecting;
        })
    });

    logoObserver.observe(logoRef.value);


})
</script>