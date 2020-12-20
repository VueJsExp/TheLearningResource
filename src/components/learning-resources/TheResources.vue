<template>
    <base-card>
        <base-button 
            v-on:click = "setSelectedTab('stored-resources')"
            v-bind:mode = "storedButtonMode"
        >Stored Resources</base-button>
        <base-button
            v-on:click = "setSelectedTab('add-resource')"
            v-bind:mode = "addButtonMode"
        >Add Resource</base-button>
    </base-card>
    <component v-bind:is = "selectedTab"></component>
</template>

<script>
import StoredResources from "./StoredResources.vue";
import AddResource from "./AddResource.vue";

export default {
    components: {
        StoredResources,
        AddResource
    },
    data()
    {
        return {
            selectedTab: "stored-resources",
            storedResources: [
                {
                    id: "official-guide",
                    title: "Official Guide",
                    description: "The official Vue.js documentation",
                    link: "https://vuejs.org"
                },
                {
                    id: "google",
                    title: "Google",
                    description: "Learn to google...",
                    link: "https://google.com"
                }
            ]
        };
    },
    provide()
    {
        return {
            storedResources: this.storedResources
        };
    },
    methods: {
        setSelectedTab(tab)
        {
            this.selectedTab = tab;
        },
        
    },
    computed: {
        storedButtonMode()
        {
            return this.selectedTab === "stored-resources" ? "" : "flat";
        },
        addButtonMode()
        {
            return this.selectedTab === "stored-resources" ? "flat" : "";
        }
    }
}
</script>