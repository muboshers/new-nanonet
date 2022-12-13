<template>
  <div class="home-blog">
    <div class="container p-4">
      <div class="row">
        <div class="col-md-12 col-sm-12 col-xs-12"></div>
      </div>

      <div class="row">
        <div
          class="col-md-4 col-sm-6 col-xs-12"
          v-for="(blog, index) in data.slice(0, 4)"
          :key="index"
        >
          <div class="single-blog">
            <div class="blog-image">
              <nuxt-link
                class="image-scale"
                :to="localePath(`/blog/${blog.id}`)"
              >
                <img
                  :src="
                    'https://consultingweb.duckdns.org/api/v1/upload/' +
                    blog.image
                  "
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
                  {{ dateFormat(blog.createdDate) }}
                </span>
              </div>

              <nuxt-link :to="localePath(`/blog/${blog.id}`)">
                <h4>
                  {{ blog.title }}
                </h4>
              </nuxt-link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HomeBlog",

  data() {
    return {
      data: [],
    };
  },
  methods: {
    async getAllBlog() {
      await fetch(
        `https://consultingweb.duckdns.org/api/v1/blog/list?lang=${this.$t(
          "requestLanguage"
        )}`
      )
        .then((res) => res.json())
        .then((d) => (this.data = d.data.content))
        .catch((err) => console.log(err.message));
    },

    dateFormat(date) {
      const newTime = new Date(date);
      return `${newTime.getDate()}/${
        newTime.getMonth() + 1
      }/${newTime.getFullYear()}`;
    },
  },

  mounted() {
    this.getAllBlog();
  },
};
</script>

<style scoped>
.home-blog {
  margin-top: 80px;
}
</style>
