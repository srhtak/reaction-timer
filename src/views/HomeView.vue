<template>
    <div class="home text-center">
        <h1 class="title-gradient">Reaction Timer</h1>
    </div>
</template>

<script>
import AOS from 'aos';
export default {
    name: 'HomeView',
    mounted() {
        AOS.init();
    },
    data() {
        return {
            showModal: false,
        };
    },
    methods: {
        toggleModal() {
            this.showModal = !this.showModal;
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
