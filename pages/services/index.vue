<template>
  <div>
    <Header />
    <PageTitle :pageTitle="$t('header.service')" />
    <Service />
    <Footer />
  </div>
</template>

<script>
import PageTitle from "~/components/PageTitle";
import Service from "~/components/Service";
import Footer from "~/components/Footer";
import Header from "~/components/Header.vue";
export default {
  name: "services",
  components: {
    Footer,
    Service,
    PageTitle,
    Header
  },
  head() {
    return {
      title: "Nanonet | Service"
    };
  }
};
</script>

<style scoped></style>
