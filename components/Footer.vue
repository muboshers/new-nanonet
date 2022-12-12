<template>
  <footer class="footer1">
    <div class="footer-area" style="background-color:#fff;">
      <div class="container">
        <div class="row">
          <div class="col-md-5 col-sm-5 col-xs-12">
            <div class="footer-content logo-footer">
              <div class="footer-head">
                <div class="footer-logo">
                  <nuxt-link class="logo" to="/">
                    <img
                      src="/img/logo/consulty-logo.jpg"
                      style=" object-fit: contain;height: 60px;"
                    />
                  </nuxt-link>
                </div>
                <h4>
                  {{ $t("footer.description") }}
                </h4>
              </div>
            </div>
          </div>
          <div class="col-md-4 col-sm-3 col-xs-12">
            <div class="footer-content">
              <div class="footer-head">
                <ul class="footer-list">
                  <li>
                    <nuxt-link :to="localePath('/')">{{
                      $t("header.home")
                    }}</nuxt-link>
                  </li>

                  <li>
                    <nuxt-link :to="localePath('/about')">{{
                      $t("header.about")
                    }}</nuxt-link>
                  </li>

                  <li>
                    <nuxt-link :to="localePath('/services')">{{
                      $t("header.service")
                    }}</nuxt-link>
                  </li>
                  <li>
                    <nuxt-link :to="localePath('/blog')">{{
                      $t("header.blog")
                    }}</nuxt-link>
                  </li>
                </ul>
              </div>
            </div>
          </div>
          <div class="col-md-3 col-sm-4 col-xs-12">
            <div class="footer-content last-content">
              <div class="footer-head">
                <h4>{{ $t("footer.contactInformation.title") }}</h4>
                <div class="footer-contacts">
                  <p>
                    <span
                      >{{ $t("footer.contactInformation.location") }} :</span
                    >
                    {{ $t("footer.address.city") }}
                  </p>
                  <p>
                    <span
                      >{{ $t("footer.contactInformation.phoneNumber") }} :</span
                    >
                    +998 90 123 77 77
                  </p>
                  <p>
                    <span>{{ $t("footer.contactInformation.email") }} :</span>
                    nanonet@gmail.com
                  </p>
                </div>
                <div class="footer-icons">
                  <ul>
                    <li>
                      <a href="#">
                        <i class="fa fa-facebook"></i>
                      </a>
                    </li>
                    <li>
                      <a href="#">
                        <i class="fa fa-twitter"></i>
                      </a>
                    </li>
                    <li>
                      <a href="#">
                        <i class="fa fa-google"></i>
                      </a>
                    </li>
                    <li>
                      <a href="#">
                        <i class="fa fa-pinterest"></i>
                      </a>
                    </li>
                    <li>
                      <a href="#">
                        <i class="fa fa-instagram"></i>
                      </a>
                    </li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="footer-area-bottom">
      <div class="container">
        <div class="row">
          <div class="col-md-6 col-sm-6 col-xs-12">
            <div class="copyright">
              <p>
                {{ $t("footer.demand") }}
              </p>
              <p>
                {{ $t("footer.developers") }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "Footer"
};
</script>

<style scoped>
@media screen and (max-width: 768px) {
  .footer-logo {
    display: none;
  }
}
</style>
