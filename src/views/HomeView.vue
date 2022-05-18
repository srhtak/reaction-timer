<template>
    <div class="flex justify-center items-center flex-col">
        <h1 class="title-gradient">Reaction Timer</h1>
        <button @click="start" :class="{ 'disable-button': isPlaying }" class="start-button">Play</button>
        <app-block v-if="isPlaying" :delay="delay" @time="endGame" />
        <p class="result-text" v-if="showResult">ms : {{ score }}</p>
    </div>
</template>

<script>
import AOS from 'aos';
import AppBlock from '../components/AppBlock.vue';
export default {
    name: 'HomeView',
    components: {
        AppBlock,
    },
    mounted() {
        AOS.init();
    },
    data() {
        return {
            isPlaying: false,
            delay: null,
            score: null,
            showResult: false,
        };
    },
    methods: {
        start() {
            this.delay = 2000 + Math.random() * 5000;
            this.isPlaying = true;
        },
        endGame(reactionTime) {
            this.score = reactionTime;
            this.isPlaying = false;
            this.showResult = true;
        },
    },
};
</script>

<style lang="scss">
body {
    background-image: url('../assets/mesh.jpeg');
    background-repeat: no-repeat;
    background-size: cover;
}
</style>
