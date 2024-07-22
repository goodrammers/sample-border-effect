<template>
    <div class="g-flex-center" style="min-height: 100vh; flex-direction: column">
        <Box
            :border-width="borderWidth"
            :height="height"
            :width="width"
            :duration="duration"
            :pause="pause"
        >
            <div class="g-flex-center content">
                <img
                    width="90%"
                    src="https://media.istockphoto.com/id/1496970435/ko/%EC%82%AC%EC%A7%84/%EC%B6%94%EC%83%81%EC%A0%81%EC%9D%B8-vr-%ED%99%98%EA%B2%BD.jpg?s=2048x2048&w=is&k=20&c=J4iz0HbChW_BohXVsXz7VhIJkNKZaJ8mkf5xPoOro3o="
                />
            </div>
        </Box>

        <div style="margin-top: 20px; color: white" class="g-flex-center">
            <div class="my-button" @click="pause = !pause">
                <span style="font-size: 40px; color: white" :class="pauseClassName"></span>
            </div>
            <div style="margin-left: 30px">속도</div>
            <input style="margin-left: 10px" v-model="duration" type="range" min="2" max="20" />
            <div style="margin-left: 10px; width: 40px">{{ duration }}</div>
        </div>
    </div>
</template>

<script setup lang="ts">
import Box from '@/components/Box.vue'
import { computed, ref } from 'vue'
const borderWidth = ref('10px')
const width = ref('500px')
const height = ref('350px')
const duration = ref(10)
const pause = ref(false)
const pauseClassName = computed(() =>
    pause.value ? 'mdi mdi-play-circle-outline' : 'mdi mdi-pause-circle-outline'
)
</script>

<style lang="scss">
body {
    background-color: black;
}
.content {
    background-color: black;
    width: 100%;
    height: 100%;
    border-radius: 20px;
}
.my-button {
    cursor: pointer;
}
</style>
