<template>
    <section v-if="showBlock" class="shadow-2xl mt-6 bg-white rounded-3xl">
        <div class="p-6 text-center sm:p-8">
            <h5 class="mt-6 text-3xl font-bold">Quickly press the button below</h5>

            <button @click="stopTimer" class="inline-block w-full py-4 mt-8 text-sm font-bold text-white bg-pink-600 rounded-full shadow-xl">Click</button>
        </div>
    </section>
</template>

<script>
export default {
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0,
        };
    },
    props: ['delay'],
    mounted() {
        setTimeout(() => {
            this.showBlock = true;
            this.startTimer();
        }, this.delay);
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10;
            }, 10);
        },
        stopTimer() {
            clearInterval(this.timer);
            this.$emit('time', this.reactionTime);
        },
    },
};
</script>

<style></style>
