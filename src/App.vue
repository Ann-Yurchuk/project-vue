<template>
  <div :id="$style.app">
    <div>
      <ApartmentsList :items="apartments" >
      <template v-slot:apartment="{apartment}">
        <ApartmentItem 
        :key="apartment.id" 
        :descr="apartment.descr" 
        :rating="apartment.rating"
        :imgSrc="apartment.imgUrl" 
        :price="apartment.price" />
      </template>
      </ApartmentsList>
    </div>
  </div>
</template>

<script>
import ApartmentItem from './components/apartment/ApartmentItem';
import ApartmentsList from "./components/apartment/ApartmentsList"
import apartments from "./components/apartment/apartments"

export default {

  name: "App",
  components: {
    ApartmentsList,
    ApartmentItem,
  },
  data() {
    return {
      apartments,
    }
  }
};
</script>

<style module>
#app {
  font-family: Arial, Helvetica, sans-serif, Montserrat;
  -webkit-font-smoothing: antialiased;
  -moz-osk-font-smoothing: grayscale;
  text-align: center;
  color: #0F1D2D;
  margin-bottom: 60px;
}
</style>
