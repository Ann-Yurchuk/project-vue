<template>
    <button v-on="listeners" v-bind:type="type" :class="{ btn: true, 'btn--outline': outlined }">
        <slot></slot>
    </button>
</template>

<script>

export default {
    name: 'ButtonComponent',
    props: {
        type: {
            type: String,
            default: 'button'
        },
        outlined: {
            type: Boolean,
            default: false
        }

    }
}
</script>

<style lang="scss" scoped>
@import "../../assets/scss/variables.scss";
.btn {
    display: inline-block;
    cursor: pointer;
    font-size: 18px;
    background-color: $main-color;
    color: #fff;
    min-width: 220px;
    padding: 8px 15px;
    border: 1px solid transparent;

    &--outline {
        background-color: transparent;
        border: 1px solid $main-color;
        color: $main-color;
    }
}
</style>