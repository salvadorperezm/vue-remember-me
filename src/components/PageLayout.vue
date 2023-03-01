<template>
    <the-header></the-header>
    <page-selector @selected-component="componentToDisplay"></page-selector>
    <component :is="currentComponent" :resources="resources"></component>
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
            resources: [
                {
                    title: 'Google',
                    description: 'You need to know how to google',
                    link: 'https://google.com'
                }
            ]
        }
    },
    methods: {
        componentToDisplay(component) {
            this.currentComponent = component
        }
    }
}
</script>

<style scoped></style>