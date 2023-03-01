<template>
    <section>
        <form @submit.prevent="addResource" class="add-resource__form">
            <label for="title" class="add-resource__label">Title</label>
            <input type="text" id="title" v-model="resource.title" class="add-resource__input" />
            <label for="description" class="add-resource__label">Description</label>
            <textarea type="text" id="description" v-model="resource.description"
                class="add-resource__text-area"></textarea>
            <label for="link" class="add-resource__label">Link</label>
            <input type="text" id="link" v-model="resource.link" class="add-resource__input" />
            <button class="add-resource__button">Add Resource</button>
        </form>
    </section>
</template>

<script>
export default {
    emits: ['new-resource'],
    data() {
        return {
            resource: {
                title: '',
                description: '',
                link: '',
            }
        }
    },
    methods: {
        addResource() {
            this.$emit('new-resource', this.resource)
        }
    }
}
</script>

<style scoped>
.add-resource__form {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
}

.add-resource__label {
    font-size: 20px;
    font-weight: bold;
    margin-block-end: 5px;
}

.add-resource__input,
.add-resource__text-area {
    width: 100%;
    margin-block-end: 20px;
}

.add-resource__text-area {
    height: 50px;
    font-family: sans-serif;
}

.add-resource__button {
    text-transform: capitalize;
    border: none;
    padding: 20px;
    color: var(--white);
    background-color: var(--purple);
    font-size: 16px;
}

.add-resource__button:hover {
    cursor: pointer;
}
</style>