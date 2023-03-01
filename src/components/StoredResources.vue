<template>
    <section v-if="resources.length > 0" v-for="resource in resources" :key="resource.id" class="resource-item">
        <div class="resource-item__header">
            <h2 class="resource-item__title">{{ resource.title }}</h2>
            <button @click="returnId(resource.id)" class="resource-item__button">Delete</button>
        </div>
        <div class="resource-item__body">
            <p class="resource-item__description">{{ resource.description }}</p>
            <a :href="resource.link" target="_blank" class="resource-item__link">View resource</a>
        </div>
    </section>
    <section v-else class="no-resource">
        <h2 class="no-resource__title">No resources yet.</h2>
        <p class="no-resource__body">Try adding some on the Add Resource page</p>
    </section>
</template>

<script>
export default {
    emits: ['return-id'],
    props: ['resources'],
    methods: {
        returnId(id) {
            this.$emit('return-id', id)
        }
    }
}
</script>

<style scoped>
.resource-item__header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-block-end: 10px;
}

.resource-item__button {
    border: none;
    background-color: var(--white);
    cursor: pointer;
    color: var(--wine);
    font-size: 16px;
    padding: 10px;
}

.resource-item__button:hover {
    color: var(--white);
    background-color: var(--wine);
    border-radius: 5px;
}

.resource-item__link {
    text-decoration: none;
    color: var(--orange);
}

.resource-item__description {
    margin-block-end: 10px;
}

.resource-item__link:hover {
    text-decoration: underline;
}

.no-resource {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.no-resource__title {
    margin-block-end: 10px;
}
</style>