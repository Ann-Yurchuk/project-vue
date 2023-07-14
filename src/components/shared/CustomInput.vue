<template>
    <input v-bind="$attrs" class="custom-input" />
</template>

<script>
export default {
    name: 'CustomInput',
    inheritAttrs: false,
    props: {
        value: {
            type: String,
            default: '',
        }
    },
    computed: {
        listeners() {
            return {
                /* eslint-disable */
                ...this.$listeners,
                input: event => this.$emit('input', event.target.value)
            }
        }
    }
}
</script>

<style lang="scss" scoped>
@import "../../assets/scss/variables.scss";

.custom-input {
    min-height: 40px;
    min-width: 220px;
    border: 2px solid $main-color;
    font-size: 18px;
    outline: none;
    line-height: inherit;
    padding: 8px 15px;

    &::placeholder {
        color: inherit;
    }
}
</style>