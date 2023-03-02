<template>
    <the-header></the-header>
    <page-selector @selected-component="componentToDisplay"></page-selector>
    <stored-resources v-if="currentComponent === 'stored-resources'" :resources="resources"
        @return-id="deleteTask"></stored-resources>
    <add-resource v-else @new-resource="addResource"></add-resource>
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
        deleteTask(id) {
            const filteredArray = this.resources.filter((resource) => resource.id !== id)
            this.resources = filteredArray
        },
        addResource(resource) {
            this.resources.push(resource)
        }
    }
}
</script>

<style scoped></style>