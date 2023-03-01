<template>
    <the-header></the-header>
    <page-selector @selected-component="componentToDisplay"></page-selector>
    <component :is="currentComponent" :resources="resources" @return-id="returnId"></component>
</template>

<script>
import PageSelector from "./PageSelector.vue";
import StoredResources from "./StoredResources.vue";
import TheHeader from "./TheHeader.vue"

export default {
    components: {
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
        }
    }
}
</script>

<style scoped></style>