<template>
  <div>
    <router-link :to="{ name: `review`, params: { code: code } }">
      <div
        class="c-country"
      >
        <div class="c-country__flag">
          <img class="c-country__flag--image" :src="flag" :alt="name" />
          <h2 class="c-country__title">{{ name }}</h2>
        </div>
        <div class="c-country__info">
          <div class="c-country__info--text">
            <span class="c-country__info--title">Capital:</span>
            <span>{{ capital }}</span>
            <span class="c-country__info--title">Region:</span>
            <span>{{ region }}</span>
            <span class="c-country__info--title">Rating:</span>
            <span>4</span>
          </div>
          <div class="c-country__image">
            <img
              :src="require(`@/assets/img/country-flags/${code}.png`)"
              width="200"
              :alt="code"
            />
          </div>
        </div>
      </div>
    </router-link>
  </div>
</template>
<script>
export default {
  name: "Country",
  props: {
    code: String,
    flag: String,
    name: String,
    capital: String,
    region: String,
  },
  methods: {},
};
</script>
<style lang="scss" scoped>
@import "@/assets/style/components/country.scss";
a {
  text-decoration: none;
}
.c-country {
  cursor: pointer;
}
</style>
