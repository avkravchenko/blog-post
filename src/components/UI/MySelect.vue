<template>
    <select 
        class="select"
        :value="modelValue" 
        @change="changeOptions">
        <option value="" disabled>Sort posts</option>
        <option 
            v-for="option in options" 
            :key="option.value"
            :value="option.value">
            {{ option.value }}
        </option>
    </select>
</template>

<script>
    export default {
        name: 'my-select',
        props: {
            modelValue: {
                type: String
            },
            options: {
                type: Array,
                default: () => []
            }
        },
        methods: {
            changeOptions(event) {
                this.$emit('update:modelValue', event.target.value);
            }
        }
    }
</script>

<style lang="scss" scoped>
    .select {
        border: none;
        color: rgb(0, 128, 255);

        &:focus {
            outline: none;
        }
    }
</style>