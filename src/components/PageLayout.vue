<template>
    <the-header></the-header>
    <page-selector @selected-component="componentToDisplay"></page-selector>
    <stored-resources v-if="currentComponent === 'stored-resources'" :resources="resources"
        @return-id="deleteTask"></stored-resources>
    <add-resource v-else @new-resource="addResource"></add-resource>
    <teleport to="body">
        <alert-toast v-if="isToastDisplayed" @close-toast="closeToast">
            <template v-slot:header>
                <h2>invalid input</h2>
            </template>
            <template v-slot:default>
                <p>Unfortunately, at least one input is invalid.</p>
                <p>Please check all inputs and make sure you enter at least a few characters into each input field.</p>
            </template>
        </alert-toast>
    </teleport>
</template>

<script>
import AddResource from "./AddResource.vue";
import PageSelector from "./PageSelector.vue";
import StoredResources from "./StoredResources.vue";
import TheHeader from "./TheHeader.vue"
import AlertToast from "./AlertToast.vue";

export default {
    components: {
        'add-resource': AddResource,
        'page-selector': PageSelector,
        'stored-resources': StoredResources,
        'the-header': TheHeader,
        'alert-toast': AlertToast,
    },
    created() {
        if (!localStorage.getItem('resources')) {
            localStorage.setItem('resources', '')
        }
    },
    mounted() {
        if (localStorage.getItem('resources') !== '') {
            this.resources = JSON.parse(localStorage.getItem('resources'))
        }
    },
    data() {
        return {
            currentComponent: '',
            resources: [],
            isToastDisplayed: false,
        }
    },
    methods: {
        componentToDisplay(component) {
            this.currentComponent = component
        },
        closeToast() {
            this.isToastDisplayed = !this.isToastDisplayed
        },
        deleteTask(id) {
            const filteredArray = this.resources.filter((resource) => resource.id !== id)
            this.resources = filteredArray
        },
        addResource(resource) {
            if (resource.title === '' || resource.description === '' || resource.link === '') {
                this.isToastDisplayed = !this.isToastDisplayed
            } else {
                this.resources.push(resource)
            }

        }
    },
    watch: {
        resources: {
            handler() {
                localStorage.setItem('resources', JSON.stringify(this.resources))
            },
            deep: true
        }
    }
}
</script>

<style scoped></style>