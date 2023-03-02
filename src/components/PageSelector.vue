<template>
    <section class="page-selector__container">
        <button :class="['page-selector__button', isComponentActive('stored-resources')]"
            @click="selectComponent('stored-resources')">stored resources</button>
        <button :class="['page-selector__button', isComponentActive('add-resources')]"
            @click="selectComponent('add-resources')">add resource</button>
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
        },
        isComponentActive(component) {
            if (this.currentComponent === component) {
                return 'page-selector__button--active'
            } else {
                return null
            }
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
    border-radius: 5px;
}

.page-selector__button:hover,
.page-selector__button--active {
    color: var(--white);
    background-color: var(--purple);
}

.page-selector__button:hover {
    cursor: pointer;
}
</style>