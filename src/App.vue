<template>
    <the-header v-bind:title = "appTitle"></the-header>
    <!-- <stored-resources v-bind:resources = "storedResources"></stored-resources>     -->
    <!-- <component></component> -->
    <the-resources></the-resources>
</template>

<script>

import TheHeader from "./components/layouts/TheHeader.vue";
import TheResources from "./components/learning-resources/TheResources.vue";

export default {
    components: {
        TheHeader,
        TheResources
    },
    data()
    {
        return {
            appTitle: "RememberMe"
        };
    }
    
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>