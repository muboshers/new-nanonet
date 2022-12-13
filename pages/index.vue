<template>
  <div>
    <Header />
    <Slider />
    <Welcome />
    <div style="margin-top:4rem;">
      <About />
    </div>
    <Service />
    <Quote />
    <HomeBlog />
    <Footer />
  </div>
</template>

<script>
import Header from "~/components/Header";
import Welcome from "~/components/Welcome";
import About from "~/components/About";
import Service from "~/components/Service";
import Quote from "~/components/Quote";
import Blog from "~/components/Blog";
import Reviews from "~/components/Reviews";
import Footer from "~/components/Footer";
import Slider from "~/components/Slider.vue";
import HomeBlog from "~/components/HomeBlog";

export default {
  components: {
    Footer,
    Reviews,
    Blog,
    Quote,
    Service,
    About,
    Welcome,
    Header,
    Slider,
    HomeBlog,
  },
  head() {
    return {
      title: "Nanonet Consulty Agency",
    };
  },

  data() {
    return {
      sliderContent: [{}],
    };
  },
};
</script>

<style></style>
