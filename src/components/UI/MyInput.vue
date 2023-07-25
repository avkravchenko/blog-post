<template>
    <input :value="modelValue" @input="updateInput" class="input" type="text">
</template>

<script>
    export default {
        name: 'my-input',
        props: {
            modelValue: [String, Number]
        },
        methods: {
            updateInput(event) {
                this.$emit('update:modelValue', event.target.value)
            }
        }
    }
</script>

<style lang="scss" scoped>
    .input {
        flex: 1;
        border: none;
        padding: 0.5rem 1rem;
        background-color: #fff;
        border-radius: 1rem;

        &:focus {
            outline: none
        }
    }
</style>