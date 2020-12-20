<template>
    <ul>
        <learning-resource
            v-for = "resource in storedResources"
            v-bind:key = "resource.id"
            v-bind:resource-title = "resource.title"
            v-bind:resource-description = "resource.description"
            v-bind:resource-link = "resource.link"
        ></learning-resource>
    </ul>
</template>

<script>

import LearningResource from "./LearningResource.vue";

export default {
    components: {
        LearningResource
    },
    inject: ["storedResources"]
}
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>