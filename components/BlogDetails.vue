<template>
  <div class="blog-area fix area-padding">
    <div class="container">
      <div class="row">
        <div class="blog-details">
          <div class="col-md-8 col-sm-8 col-xs-12">
            <article class="blog-post-wrapper">
              <div class="blog-banner">
                <a href="#" class="blog-images">
                  <img
                    :src="
                      'http://consultingweb.duckdns.org/api/v1/upload/' +
                      singleBlog.image
                    "
                    alt=""
                  />
                </a>
                <div class="blog-content">
                  <div class="blog-meta">
                    <span class="admin-type">
                      <i class="fa fa-user"></i>
                      {{ singleBlog.author }}
                    </span>
                    <span class="date-type">
                      <i class="fa fa-calendar"></i>
                      {{ dateFormat(singleBlog.createdDate) }}
                    </span>
                    <span class="comments-type">
                      <i class="fa fa-comment-o"></i>
                      07
                    </span>
                  </div>
                  <h4>{{ singleBlog.title }}</h4>
                  <p>
                    {{ singleBlog.description }}
                  </p>
                </div>
              </div>
            </article>
            <div class="clear"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "BlogDetails",

  props: {
    singleBlog: Object,
  },

  methods: {
    dateFormat(date) {
      const newTime = new Date(date);
      return `${newTime.getDate()}/${
        newTime.getMonth() + 1
      }/${newTime.getFullYear()}`;
    },
  },
};
</script>

<style scoped></style>
