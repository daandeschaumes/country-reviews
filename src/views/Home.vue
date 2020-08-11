<template>
<main>
  <container>
    <row>
      <h1>Home</h1>
    </row>
    <row>
      <p class="c-textarea">There are some beautiful countries on this earth.<br />
Explore which ones are worth a visit!</p>
    </row>
    <row>
      <grid>
        <country-card  v-for="c in countries" :key="c.alpha2Code"  :capital="c.capital" :name="c.name" :code="c.alpha2Code" :flag="c.flag" :region="c.region"/>
      </grid>
    </row>
  </container>

</main>
</template>

<script>
import Container from '@/components/layout/Container';
import Row from '@/components/layout/Row';
import Grid from "@/components/layout/Grid";
import CountryCard from "@/components/CountryCard";

export default {
  name: 'home',
  computed:{
    countries(){
      return this.$store.state.countries;
    }
  },
  created(){
    this.$store.dispatch('getCountries');
  },
  components: {
    Container,
    Row,
    Grid,
    CountryCard
    
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/style/components/textarea.scss';

</style>
