<template>
  <div :id="$style.app">
    <h2>{{ text }}</h2>
    <CustomSelect :items="['name', 'label', 'salary']" />
    <CustomInput v-model="text" />
    <ApartmentsList :items="apartments">
      <template v-slot:apartment="{ apartment }">
        <ApartmentItem 
        :key="apartment.id" 
        :descr="apartment.descr" 
        :rating="apartment.rating" 
        :imgSrc="apartment.imgUrl"
        :price="apartment.price" 
        @click="handelItemClick" />
      </template>
    </ApartmentsList>
  </div>
</template>

<script>
import ApartmentItem from "./components/apartment/ApartmentItem";
import ApartmentsList from "./components/apartment/ApartmentsList";
import apartments from "./components/apartment/apartments";
import CustomInput from "./components/shared/CustomInput.vue";
import CustomSelect from "./components/shared/CustomSelect.vue";

export default {
  name: "App",
  components: {
    ApartmentsList,
    ApartmentItem,
    CustomInput,
    CustomSelect,
  },
  data() {
    return {
      apartments,
      text: "",
    };
  },
  methods: {
    handelItemClick() {
      console.log("item click");
    },
  },
};
</script>

<style module>
#app {
  font-family: Arial, Helvetica, sans-serif, Montserrat;
  -webkit-font-smoothing: antialiased;
  -moz-osk-font-smoothing: grayscale;
  text-align: center;
  color: #0f1d2d;
  margin-bottom: 60px;
}
</style>
