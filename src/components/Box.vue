<template>
    <div class="box-container g-relative">
        <div class="box-border-effect"></div>
        <div class="g-abs-full" style="padding: 20px; z-index: 2">
            <slot></slot>
        </div>
    </div>
</template>

<script setup lang="ts">
import { computed, toRefs } from 'vue'

const p = defineProps<{ width?: string; height?: string; borderWidth?: string }>()
const { width: _width, height: _height, borderWidth: _borderWidth } = toRefs(p)
const width = computed(() => (_width.value ? _width.value : '200px'))
const height = computed(() => (_height.value ? _height.value : '200px'))
const borderWidth = computed(() => (_borderWidth.value ? _borderWidth.value : '6px'))
</script>

<style lang="scss" scoped>
@property --border-effect-deg {
    syntax: '<angle>';
    inherits: false;
    initial-value: 0deg;
}
@keyframes animate {
    0% {
        --border-effect-deg: 0deg;
    }
    100% {
        --border-effect-deg: 360deg;
    }
}
.box-border-effect {
    position: relative;
    width: v-bind(width);
    height: v-bind(height);
    background: repeating-conic-gradient(
        from var(--border-effect-deg),
        #ff2770 0% 5%,
        transparent 5% 144deg,
        #ff2770 180deg
    );
    animation: animate 4s linear infinite;
    border-radius: 20px;
    &:before {
        content: '';
        position: absolute;
        width: 100%;
        height: 100%;
        background: repeating-conic-gradient(
            from var(--border-effect-deg),
            #45f3ff 0%,
            #45f3ff 5%,
            transparent 5%,
            transparent 40%,
            #45f3ff 50%
        );
        animation: animate 4s linear infinite;
        animation-delay: -1s;
        border-radius: 20px;
    }
    &:after {
        content: '';
        position: absolute;
        background: white;
        z-index: 1;
        inset: 10px;
        border-radius: 16px;
    }
}
</style>
