<template>
    <div class="g-flex-center" style="min-height: 100vh">
        <Box :border-width="borderWidth">
            <div class="g-flex-center" style="height: 100%">Hello</div>
        </Box>
    </div>
</template>

<script setup lang="ts">
import Box from '@/components/Box.vue'
import { ref } from 'vue'
const borderWidth = ref('10px')
</script>

<style scoped></style>
