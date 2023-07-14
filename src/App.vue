<template>
  <div id="app">
    <Container>
      <ApartmentFilterForm class="apartment-filter" @submit="logger" />
      <ApartmentsList :items="apartments">
        <template v-slot:apartment="{ apartment }">
          <ApartmentItem :key="apartment.id" :descr="apartment.descr" :rating="apartment.rating"
            :imgSrc="apartment.imgUrl" :price="apartment.price" />
        </template>
      </ApartmentsList>
    </Container>
  </div>
</template>

<script>
import ApartmentItem from "./components/apartment/ApartmentItem";
import ApartmentsList from "./components/apartment/ApartmentsList";
import apartments from "./components/apartment/apartments";
import ApartmentFilterForm from "./components/apartment/ApartmentFilterForm.vue";
import Container from "./components/shared/Container.vue";

export default {
  name: "App",
  components: {
    ApartmentsList,
    ApartmentItem,
    ApartmentFilterForm,
    Container
  },
  data() {
    return {
      apartments,
      text: "",
    };
  },
  methods: {
    logger(value) {
      console.log(value);
    },
  },
};
</script>

<style lang="scss" scoped>
#app {
  font-family: Arial, Helvetica, sans-serif, Montserrat;
  -webkit-font-smoothing: antialiased;
  -moz-osk-font-smoothing: grayscale;
  text-align: center;
  color: #0f1d2d;
  margin-bottom: 60px;
}

.apartment-filter {
  margin-bottom: 40px;
}
</style>
