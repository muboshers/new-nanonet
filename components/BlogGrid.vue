<template>
  <div class="blog-area fix area-padding-2">
    <div class="container">
      <div class="row">
        <div class="col-md-12 col-sm-12 col-xs-12">
          <div class="section-headline text-center">
            <h3>{{ $t("header.blog") }}</h3>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="blog-grid home-blog">
          <div
            class="col-md-4 col-sm-6 col-xs-12"
            v-for="(blog, index) in data"
            :key="index"
          >
            <div class="single-blog">
              <div class="blog-image">
                <nuxt-link class="image-scale" to="/">
                  <img
                    :src=" 'http://consultingweb.duckdns.org/api/v1/upload/' + blog.image"
                    alt="blog.title"
                  />
                </nuxt-link>
              </div>
              <div class="blog-content">
                <div class="blog-meta">
                  <span class="admin-type">
                    <i class="fa fa-user"></i>
                    {{ blog.author }}
                  </span>
                  <span class="date-type">
                    <i class="fa fa-calendar"></i>
                    {{ blog.createdDate }}
                  </span>
                </div>
                <a href="#">
                  <h4>
                    {{ blog.title }}
                  </h4>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "BlogGrid",

  data() {
    return {
      data: []
    };
  },
  methods: {
    async getAllBlog() {
      await fetch(
        `https://consultingweb.duckdns.org/api/v1/blog/list?lang=${this.$t(
          "requestLanguage"
        )}`
      )
        .then(res => res.json())
        .then(d => (this.data = d.data.content))
        .catch(err => console.log(err.message));
    }
  },

  mounted() {
    this.getAllBlog();
  }
};
</script>

<style scoped></style>
