<style scoped>
.green {
    @apply text-green-500
}

.orange {
    @apply text-orange-500
}
</style>
<template>
    <div class="flex flex-col gap-2 justify-center overflow-hidden  relative">
        <h2 class="text-lg font-semibold transition-transform" :class="computedLabelClass">{{ title }}</h2>
        <h3 class="text-4xl " :class="computedTextClass">
            <span class="transition-opacity ease-out" :class="showPreSuffix ? 'opacity-100' : 'opacity-0'">{{ prefix
            }}</span>
            {{ animatedText }}
            <span class="transition-opacity ease-out" :class="showPreSuffix ? 'opacity-100' : 'opacity-0'">
                {{ suffix }}
            </span>
        </h3>
    </div>
</template>
<script setup>

const formatter = new Intl.NumberFormat('en-NZ', {
    minimumFractionDigits: 0,
    maximumFractionDigits: 2,
    trailingZeroDisplay: 'stripIfInteger'
});

const props = defineProps({
    textColor: {
        type: String,
        default: 'green'
    },
    title: String,
    value: Number,
    prefix: String,
    suffix: String,
    order: Number,
    isIntersecting: Boolean
});

const animatedValue = ref(0);
const animatedText = computed(() => {
    return formatter.format(animatedValue.value)
})

const show = ref(false);
const showPreSuffix = ref(false);
const computedTextClass = computed(() => {
    return `${props.textColor} ${show.value ? 'opacity-100' : 'opacity-0'}`
});

const computedLabelClass = computed(() => {
    return show.value ? 'translate-y-0' : 'translate-y-4	'
});

const steps = 100;
const perValue = props.value / steps;
const perValueRounded = Math.floor(props.value) === props.value
    ? Math.round(perValue)
    : perValue;

function addToAnimatedValue() {
    animatedValue.value = Math.min(animatedValue.value + perValueRounded, props.value);
    if (animatedValue.value >= props.value) {
        showPreSuffix.value = true;
        return;
    }
    requestAnimationFrame(addToAnimatedValue);
}

watch(show, () => {
    if (!show.value || !props.value) return;
    requestAnimationFrame(addToAnimatedValue)
})

watch(props, () => {
    if (!props.isIntersecting) return;
    setTimeout(() => {
        show.value = true;
    }, 300 * props.order)
})
</script>