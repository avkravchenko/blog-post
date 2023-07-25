<template>
    <button class="btn">
        <slot></slot>
    </button>
</template>

<script>
    export default {
        name: 'my-button'
    }
</script>

<style lang="scss" scoped>
.btn {
    background-color: rgb(255, 255, 255);
    border-radius: 1rem;
    border: none;
    color: rgb(0, 128, 255);
    padding: .5rem 1rem;
}
</style>