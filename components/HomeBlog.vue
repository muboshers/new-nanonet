<template>
  <div class="home-blog">
    <div class="container p-4">
      <div class="row">
        <div class="col-md-12 col-sm-12 col-xs-12">
          <div class="section-headline text-center">
            <h3>Technology news</h3>
            <p>
              Dummy text is also used to demonstrate the appearance of different
              typefaces and layouts
            </p>
          </div>
        </div>

        <div class="row">
          <div class="col-md-4 col-sm-6 col-xs-12">
            <div class="single-blog">
              <div class="blog-image">
                <a class="image-scale" href="#">
                  <img src="/img/blog/b1.jpg" alt="" />
                </a>
              </div>
              <div class="blog-content">
                <div class="blog-meta">
                  <span class="admin-type">
                    <i class="fa fa-user"></i>
                    Admin
                  </span>
                  <span class="date-type">
                    <i class="fa fa-calendar"></i>
                    20 july, 2019
                  </span>
                  <span class="comments-type">
                    <i class="fa fa-comment-o"></i>
                    13
                  </span>
                </div>
                <a href="#">
                  <h4>
                    Creative design clients response is better
                  </h4>
                </a>
              </div>
            </div>
          </div>

          <div class="col-md-4 col-sm-6 col-xs-12">
            <div class="single-blog">
              <div class="blog-image">
                <a class="image-scale" href="#">
                  <img src="/img/blog/b2.jpg" alt="" />
                </a>
              </div>
              <div class="blog-content">
                <div class="blog-meta">
                  <span class="admin-type">
                    <i class="fa fa-user"></i>
                    Admin
                  </span>
                  <span class="date-type">
                    <i class="fa fa-calendar"></i>
                    13 may, 2018
                  </span>
                  <span class="comments-type">
                    <i class="fa fa-comment-o"></i>
                    16
                  </span>
                </div>
                <a href="#">
                  <h4>
                    We're Committed to People, Committed to the Future.
                  </h4>
                </a>
              </div>
            </div>
          </div>
          <div class="col-md-4 col-sm-6 col-xs-12">
            <div class="single-blog">
              <div class="blog-image">
                <a class="image-scale" href="#">
                  <img src="/img/blog/b3.jpg" alt="" />
                </a>
              </div>
              <div class="blog-content">
                <div class="blog-meta">
                  <span class="admin-type">
                    <i class="fa fa-user"></i>
                    Admin
                  </span>
                  <span class="date-type">
                    <i class="fa fa-calendar"></i>
                    24 april, 2019
                  </span>
                  <span class="comments-type">
                    <i class="fa fa-comment-o"></i>
                    07
                  </span>
                </div>
                <a href="#">
                  <h4>
                    Simple Solutions for Complex Connections
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
  name: "HomeBlog"
};
</script>

<style scoped>
.home-blog {
  margin-top: 80px;
}
</style>
