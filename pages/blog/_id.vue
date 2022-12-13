<template>
  <div>
    <Header />
    <PageTitle :pageTitle="data.title" />
    <BlogDetails :singleBlog="data" />
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
    Header,
  },

  data() {
    return {
      data: [],
    };
  },
  head() {
    return {
      title: `Nanonet | Blog Details ${this.data.title}`,
      meta: [
        {
          hid: "description",
          name: "description",
          content: this.data.description,
        },

        { hid: "author", name: "author", content: this.data.author },
        {
          hid: "og:image",
          name: "og:image",
          content: `https://consultingweb.duckdns.org/api/v1/upload/${this.data.image}`,
        },
        { hid: "og:image:width", name: "og:image:width", content: "1200" },
        {
          hid: "og:image:height",
          name: "og:image:height",
          content: "600",
        },
      ],
    };
  },
  methods: {
    async getBlogById() {
      const { id } = this.$route.params;
      await fetch(
        `https://consultingweb.duckdns.org/api/v1/blog/${id}?lang=${this.$t(
          "requestLanguage"
        )}`
      )
        .then((res) => res.json())
        .then((d) => (this.data = d.data))
        .catch((err) => console.log(err.message));
    },
  },

  mounted() {
    this.getBlogById();
  },
};
</script>

<style scoped></style>
