<template>
    <the-header></the-header>
    <page-selector @selected-component="componentToDisplay"></page-selector>
</template>

<script>
import PageSelector from "./PageSelector.vue";
import TheHeader from "./TheHeader.vue"

export default {
    components: {
        'page-selector': PageSelector,
        'the-header': TheHeader
    },
    methods: {
        componentToDisplay(component) {
            console.log('component to display: ', component)
        }
    }
}
</script>

<style scoped></style>