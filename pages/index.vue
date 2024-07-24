<template>
    <div class="container">
        <div
            class="slider"
            style="--width: 150px; --height: 150px; --quantity: 5"
        >
            <div class="slider-list">
                <div
                    v-for="i in 5"
                    :key="i"
                    :style="`--position: ${i}`"
                    class="item"
                >
                    <img
                        :src="`/assets/image/sample1.jpeg`"
                        alt="slider image"
                    />
                </div>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts"></script>

<style scoped>
.container {
    padding: 10rem;
    overflow: hidden;
    width: 100%;
    margin: auto;
}

.slider {
    width: 700px;
    height: var(--height);
    overflow: hidden;
}

.slider .slider-list {
    display: flex;
    width: 100%;
    position: relative;
}

.slider .slider-list .item {
    width: var(--width);
    height: var(--height);
    position: absolute;
    left: 100%;
    animation: autoRun 15s linear infinite;
    transition: filter 0.5s;
    animation-delay: calc((15s / var(--quantity)) * (var(--position) - 1)) !important;
}

.slider .slider-list .item img {
    width: 100%;
}

@keyframes autoRun {
    from {
        left: 100%;
    }
    to {
        left: calc(var(--width) * -1);
    }
}

.slider:hover .item {
    animation-play-state: paused !important;
    filter: grayscale(1);
}

.slider .item:hover {
    filter: grayscale(0);
}
</style>
