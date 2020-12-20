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
    <keep-alive>
        <component v-bind:is = "selectedTab"></component>
    </keep-alive>
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
            storedResources: this.storedResources,
            addNewResource: this.addNewResource,
            deleteResource: this.deleteResource
        };
    },
    methods: {
        setSelectedTab(tab)
        {
            this.selectedTab = tab;
        },
        addNewResource(newTitle, newDescription, newLink)
        {
            const newResource = {
                id: new Date().toISOString(),
                title: newTitle,
                description: newDescription,
                link: newLink
            };
            this.storedResources.unshift(newResource);
            this.selectedTab = "stored-resources";
        },
        deleteResource(resourceId)
        {
            // const foundResource = this.storedResources.find((resource) => resourceId === resource.id);
            // let index = this.storedResources.map((resource) => resource.id).indexOf(foundResource);
            // const index = this.storedResources.find((resource) => resourceId === resource.id);
            // this.storedResources.splice(index, 1);
            // this.storedResources = this.storedResources.filter((resource) => resourceId !== resource.id);
            // console.log("resources length = "+this.storedResources.length);
            // let index = 0;
            // this.storedResources.map((resource) => {
            //     if (resource)
            // })

            // let index = this.storedResources.map((resource) => resource.id).indexOf(resourceId);

            // let index = 0;
            // this.storedResources.map((resource,resIndex) => {
            //     if (resource.id === resourceId)
            //         index = resIndex;
            // });
            const index = this.storedResources.findIndex((resource) => resourceId === resource.id);
            this.storedResources.splice(index, 1);

        }
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