<template>
    <the-header></the-header>
    <page-selector @selected-component="componentToDisplay"></page-selector>
    <component :is="currentComponent" :resources="resources" @return-id="returnId" @new-resource="addResource"></component>
</template>

<script>
import AddResource from "./AddResource.vue";
import PageSelector from "./PageSelector.vue";
import StoredResources from "./StoredResources.vue";
import TheHeader from "./TheHeader.vue"

export default {
    components: {
        'add-resource': AddResource,
        'page-selector': PageSelector,
        'stored-resources': StoredResources,
        'the-header': TheHeader
    },
    data() {
        return {
            currentComponent: '',
            resources: []
        }
    },
    methods: {
        componentToDisplay(component) {
            this.currentComponent = component
        },
        returnId(id) {
            console.log(id)
        },
        addResource(resource) {
            this.resources.push(resource)
        }
    }
}
</script>

<style scoped></style>