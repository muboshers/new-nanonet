<template>
  <div>
    <Header />
    <PageTitle :pageTitle="$t('header.blog')" />
    <About />
    <BlogGrid />
    <Reviews />
    <Footer />
  </div>
</template>

<script>
import PageTitle from "~/components/PageTitle";
import BlogGrid from "~/components/BlogGrid";
import Footer from "~/components/Footer";
import Header from "~/components/Header";
import About from "~/components/About";
import Reviews from "~/components/Reviews";
export default {
  name: "blog",
  components: {
    Footer,
    BlogGrid,
    PageTitle,
    Header,
    About,
    Reviews,
  },
  head() {
    return {
      title: "Nanonet | Blog",
    };
  },
};
</script>

<style scoped></style>
