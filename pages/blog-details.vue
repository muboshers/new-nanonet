<template>
  <div>
    <Header />
    <PageTitle pageTitle="Blog Details" />
    <BlogDetails />
    <Footer />
  </div>
</template>

<script>
import PageTitle from "~/components/PageTitle";
import BlogDetails from "~/components/BlogDetails";
import Footer from "~/components/Footer";
import Header from "~/components/Header.vue";
export default {
  name: "blog-details",
  components: {
    Footer,
    BlogDetails,
    PageTitle,
    Header
  },
  head() {
    return {
      title: "Nanonet | Blog Details"
    };
  }
};
</script>

<style scoped></style>
