<template>
    <select v-bind="$attrs" class="custom-select">
        <option v-for="item in formatedItems" :key="item.value" :value="item.value" :selected="item.selected">
            {{ item.label }}</option>
    </select>
</template>

<script>
export default {
    name: "CustomSelect",
    inheritAttrs: false,
    props: {
        items: {
            type: Array,
            required: true,
        },
    },
    computed: {
        listeners() {
            return {
                /* eslint-disable */
                ...this.$listeners,
                input: (event) => this.$emit("input", event.target.value),
            };
        },
        formatedItems() {
            return this.items.map((item) => {
                return typeof item === "object" ? item : { value: item, label: item };
            });
        },
    },
};
</script>

<style lang="scss" scoped>
@import "../../assets/scss/variables.scss";

.custom-select {
    min-height: 40px;
    min-width: 220px;
    border: 2px solid $main-color;
    font-size: 18px;
    outline: none;
    line-height: inherit;
    padding: 8px 15px;
    cursor: pointer;
    display: inline-block;
}
</style>
