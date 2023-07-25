<template>
    <div class="dialog" @click="hideDialog" v-if="show">
        <div @click.stop class="dialog__content">
            <slot></slot>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'my-dialog',
        props: {
            show: {
                type: Boolean,
                default: false
            }
        },
        methods: {
            hideDialog() {
                this.$emit('update:show', false)
            }
        }
    }
</script>

<style lang="scss" scoped>
.dialog {
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 1;
    display: flex;
    position: fixed;
    background-color: rgba($color: #000000, $alpha: .5);

    .dialog__content {
        margin: auto;
        background-color: #fff;
        border-radius: 1rem;
        min-width: 350px;

    }
}
</style>