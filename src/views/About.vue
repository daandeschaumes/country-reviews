<template>
  <container>
    <h1>This is an about page</h1>
    <row>
      <span>Explore different countries, leave a review and a score</span>
    </row>
  </container>
</template>
<script>
import Container from "@/components/layout/Container";
import Row from "@/components/layout/Row";
export default {
  name: "About",
  components: {
    Container,
    Row,
  },
};
</script>
