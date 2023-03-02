<template>
    <section class="page-selector__container">
        <button class="page-selector__button" @click="selectComponent('stored-resources')">stored resources</button>
        <button class="page-selector__button" @click="selectComponent('add-resource')">add resource</button>
    </section>
</template>

<script>
export default {
    created() {
        this.$emit('selected-component', this.currentComponent)
    },
    emits: ['selected-component'],
    data() {
        return {
            currentComponent: 'stored-resources'
        }
    },
    methods: {
        selectComponent(component) {
            this.currentComponent = component
            this.$emit('selected-component', this.currentComponent)
        }
    }
}
</script>

<style scoped>
.page-selector__button:first-child {
    margin-inline-end: 10px;
}

.page-selector__button {
    text-transform: capitalize;
    border: none;
    padding: 20px;
    color: var(--purple);
    background-color: var(--white);
    font-size: 20px;

}

.page-selector__button:hover {
    color: var(--white);
    background-color: var(--purple);
    cursor: pointer;
}
</style>