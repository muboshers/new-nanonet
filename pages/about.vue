<template>
  <div>
    <Header />
    <PageTitle :pageTitle="$t('header.about')" />
    <Welcome />
    <About />
    <Reviews />
    <Footer />
  </div>
</template>

<script>
import Header from "~/components/Header.vue";
import Welcome from "~/components/Welcome";
import PageTitle from "~/components/PageTitle";
import About from "~/components/About";
import OverView from "~/components/OverView";
import Reviews from "~/components/Reviews";
import Footer from "~/components/Footer";
export default {
  name: "about",
  components: {
    Footer,
    Reviews,
    OverView,
    About,
    Welcome,
    PageTitle,
    Header
  },
  head() {
    return {
      title: "Nanonet | About Us"
    };
  }
};
</script>

<style scoped></style>
