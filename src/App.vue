<template>
    <div id="app">
        <CustomTitle :titleText="message" :subtitleText="subMessage"/>
        <img alt="Vue logo" src="./assets/logo.png" />
        <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->

    </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import CustomTitle from "./components/CustomTitle.vue";

export default {
    name: "App",
    components: {
        // HelloWorld
        CustomTitle
    },
    data() {
        return {
            message: "La mia prima app in Vue.js!",
            subMessage: "Giochiamo con le API"
        }
    }
};
</script>

<style lang="scss">
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
