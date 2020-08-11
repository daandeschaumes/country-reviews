<template>
  <container>
    <grid>
      <div class="c-card" v-for="r in reviews" :key="r.countryName">
        <h1>{{ r.countryName }}</h1>
        <span><b>Name: </b>{{ r.name }}</span
        ><br />
        <span><b>Score:</b> {{ r.score }} </span>
        <p>{{ r.text }}</p>
      </div>
    </grid>
  </container>
</template>
<style lang="scss" scoped></style>
<script>
import Container from "@/components/layout/Container";
import Row from "@/components/layout/Row";
import Grid from "@/components/layout/Grid";
export default {
  data() {
    return {
      reviews: [],
    };
  },
  components: {
    Container,
    Row,
    Grid,
  },
  created() {
    var array = localStorage.getItem("reviews");
    this.reviews = JSON.parse(array);
  },
};
</script>

<style lang="scss">
.c-card {
  -webkit-box-shadow: 4px 0px 5px 0px rgba(0, 0, 0, 0.49);
  -moz-box-shadow: 4px 0px 5px 0px rgba(0, 0, 0, 0.49);
  box-shadow: 4px 0px 5px 0px rgba(0, 0, 0, 0.49);
  max-width: 250px;
  text-align: start;
  overflow-y: scroll;
  height: 250px;
  margin-bottom: 15px;
  padding-left: 5px;
}
</style>
