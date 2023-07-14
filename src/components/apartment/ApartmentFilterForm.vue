<template>
    <form class="form" @submit.prevent="handleSubmit">
        <CustomSelect :items="cities" v-model="city" class="form__select" />
        <CustomInput v-model="price" placeholder="Ціна, від" />
        <ButtonComponent class="form__submit" type="submit">Підбір житла</ButtonComponent>
    </form>
</template>

<script>
import CustomSelect from '../shared/CustomSelect.vue';
import CustomInput from '../shared/CustomInput.vue';
import ButtonComponent from '../Btn.vue';

export default {
    name: 'ApartmentFilterForm',
    components: {
        CustomSelect,
        CustomInput,
        ButtonComponent,
    },
    data() {
        return {
            price: '',
            city: ''
        }
    },
    computed: {
        cities() {
            return [{ value: '', label: 'Місто', selected: true }, 'Kyiv', 'Odessa', 'Kharkiv', 'Ternopol', 'Lviv', 'Cherkasy', 'Poltava']


        }
    },
    methods: {
        handleSubmit() {
            this.$emit('submit', {city: this.city, price: this.price})
        }
    }
}
</script>

<style lang="scss" scoped>
.form {
    display: flex;

    &__select {
        margin-right: 30px;
    }

    &__submit {
        margin-left: auto;
    }
}
</style>