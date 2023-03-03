<template>
    <div class="toast__background">
        <div class="toast__container">
            <div class="toast__header">
                <slot name="header"></slot>
            </div>
            <div class="toast__body">
                <slot></slot>
                <button class="toast__button" @click="closeToast">okay</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    emits: ['close-toast'],
    methods: {
        closeToast() {
            this.$emit('close-toast')
        }
    }
}
</script>

<style scoped>
.toast__background {
    background-color: rgba(0, 0, 0, .4);
    position: fixed;
    top: 0px;
    z-index: 999;
    height: 100vh;
    width: 100vw;
    display: flex;
    align-items: center;
    justify-content: center;
}

.toast__container {
    flex: 1;
    border-radius: 5px;
    overflow: hidden;
    max-width: 800px;
    box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
}

.toast__header {
    background-color: var(--purple);
    color: var(--white);
    padding: 16px;
    text-transform: capitalize;
    font-size: 22px;
}

.toast__body {
    background-color: var(--white);
    color: var(--black);
    font-weight: bold;
    padding: 32px 16px;
    display: flex;
    flex-direction: column;
    gap: 20px;
}

.toast__button {
    align-self: flex-end;
    text-transform: capitalize;
    border: none;
    padding: 20px;
    color: var(--white);
    background-color: var(--purple);
    font-size: 16px;
    border-radius: 5px;
}

.toast__button:hover {
    cursor: pointer;
}
</style>