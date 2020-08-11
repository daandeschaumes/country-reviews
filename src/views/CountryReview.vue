<template>
  <container>
    <h1>{{ country.name }}</h1>
    <row>
      <div style="display: flex; flex-direction: column; align-items:center;">
        <country-card
          :capital="country.capital"
          :name="country.name"
          :code="country.alpha2Code"
          :flag="country.flag"
          :region="country.region"
        ></country-card>
        <div class="c-review-form">
          <form v-on:submit.prevent="submit" class="c-form">
            <label for="name">Name</label>
            <input
              type="text"
              placeholder="Your name"
              v-model.lazy="review.name"
            />
            <label for="review">Write your review</label>
            <textarea
              name="review"
              id="review"
              cols="30"
              rows="10"
              v-model.lazy="review.text"
            ></textarea>
            <label for="score">Score</label>
            <input
              type="number"
              placeholder="Give a score from 0 - 5"
              v-model.lazy="review.score"
              min="0"
              max="5"
            />
            <input type="submit" value="submit" />
          </form>
        </div>
      </div>
    </row>
  </container>
</template>
<script>
import CountryCard from "@/components/CountryCard.vue";
import Container from "@/components/layout/Container";
import Row from "@/components/layout/Row";
export default {
  name: "CountryReview",
  components: {
    CountryCard,
    Container,
    Row,
  },
  data() {
    return {
      country: null,
      review: {
        countryName: "",
        name: "",
        text: "",
        score: 0,
      },
    };
  },
  created() {
    this.getCountry();
    // await this.getCountry();
  },
  methods: {
    async getCountry() {
      const request = await fetch(
        `https://restcountries.eu/rest/v2/alpha/${this.$route.params.code}`
      );
      const data = await request.json();
      this.country = data;
    },
    submit(e) {
      e.preventDefault();
      this.addToLocalStorage();
      window.location.reload();
      //   localStorage.setItem("reviews", JSON.stringify(this.reviewsArr));
    },
    addToLocalStorage() {
      var a = [];

      // Parse the serialized data back into an aray of objects
      a = JSON.parse(localStorage.getItem("reviews")) || [];
      // Push the new data (whether it be an object or anything else) onto the array
      this.review.countryName = this.country.name;
      a.push(this.review);
      // Alert the array value
      alert(
        `Your review ${JSON.stringify(this.review)} was processed succesfully`
      ); // Should be something like [Object array]
      // Re-serialize the array back into a string and store it in localStorage
      localStorage.setItem("reviews", JSON.stringify(a));
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/assets/style/components/country.scss";
.c-country-review {
  display: flex;
}

.c-form {
  display: flex;
  flex-direction: column;
  align-self: flex-end;
  right: 0;
  min-width: 500px;
}
.c-form label {
  text-align: start;
}
.c-form input {
  margin-bottom: 15px;
}
</style>
