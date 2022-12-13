<template>
  <header class="header-one">
    <div
      id="sticker"
      class="header-area hidden-xs"
      style="background-color: #fff;"
    >
      <div class="container">
        <div class="row">
          <div class="col-md-3 col-sm-3">
            <div class="logo">
              <nuxt-link
                class="navbar-brand page-scroll logo"
                :to="localePath('/')"
              >
                <img
                  src="/img/logo/consulty-logo.png"
                  style=" height: 60px; object-fit: contain;"
                />
              </nuxt-link>
            </div>
          </div>
          <div class="col-md-9 col-sm-9">
            <nav class="navbar navbar-default">
              <div class="collapse navbar-collapse" id="navbar-example">
                <div class="main-menu">
                  <ul class="nav navbar-nav navbar-right">
                    <li>
                      <a class="pages" href="#">{{ $t("lang") }}</a>
                      <ul class="sub-menu">
                        <li
                          v-for="(lang, index) of languages"
                          :key="index"
                          @click="switchLanguage(lang.title)"
                        >
                          <a>{{ lang.name }}</a>
                        </li>
                      </ul>
                    </li>
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
            </nav>
          </div>
        </div>
      </div>
    </div>
    <!-- MOBILE NAVBAR -->
    <div class="mobile-menu-area hidden-lg hidden-md hidden-sm">
      <div class="container">
        <div class="row">
          <div class="col-md-12">
            <div class="mobile-menu">
              <div class="header">
                <div class="logo">
                  <nuxt-link to="/">
                    <img
                      src="/img/logo/consulty-logo.jpg"
                      style=" object-fit: contain;"
                    />
                  </nuxt-link>
                </div>
                <span>
                  <a
                    class="pages"
                    href="#"
                    @click="isLanguageActive = !isLanguageActive"
                    >{{ $t("lang") }}</a
                  >
                  <ul
                    class="sub-menu"
                    :class="isLanguageActive ? 'active' : ''"
                  >
                    <li v-for="(lang, index) of languages" :key="index">
                      <a v-on:click="switchLanguage(lang.title)">{{
                        lang.name
                      }}</a>
                    </li>
                  </ul>
                </span>
                <button class="hide-toggle-btn" @click="handleToggle">
                  <i v-if="isNavbar" class="fa fa-times" aria-hidden="true"></i>
                  <i v-else class="fa fa-bars" aria-hidden="true"></i>
                </button>
              </div>
              <div
                class="navbar-list-droptoggle"
                :class="isNavbar ? 'active' : ''"
              >
                <nav id="dropdown">
                  <ul>
                    <li>
                      <nuxt-link :to="localePath('/')">Home</nuxt-link>
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
                </nav>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  mounted() {
    var windows = $(window);
    var sticky = $("#sticker");

    windows.on("scroll", function () {
      var scroll = windows.scrollTop();
      if (scroll < 300) {
        sticky.removeClass("stick");
      } else {
        sticky.addClass("stick");
      }
    });
  },

  data() {
    return {
      isLanguageActive: false,
      isNavbar: false,
      languages: [
        {
          name: "ENG",
          title: "en",
        },
        {
          name: "RUS",
          title: "ru",
        },
        {
          name: "UZB",
          title: "uz",
        },
      ],
    };
  },
  methods: {
    switchLanguage(lang) {
      this.$i18n.setLocale(lang);
      this.isLanguageActive = !this.isLanguageActive;
    },
    handleToggle() {
      this.isLanguageActive = false;
      this.isNavbar = !this.isNavbar;
    },
  },
};
</script>

<style scoped>
.mobile-menu {
  position: fixed;
  width: 100%;
  left: 0;
  background: #fff;
  padding: 15px;
  top: 0;
}

a {
  color: #000 !important;
}

a:hover {
  color: #000016 !important;
}

.mobile-menu .header {
  display: flex;
  align-items: center;
  justify-content: flex-end;
}
.mobile-menu .header span {
  position: relative;
}

.mobile-menu .header span ul {
  position: absolute;
  background-color: #fff;
  padding: 4px 10px;
  clip-path: polygon(0 0, 100% 0, 100% 0, 9% 0);
}

.mobile-menu .header span ul li a {
  cursor: pointer;
}
.mobile-menu .header span ul.active {
  clip-path: polygon(0 0, 100% 0, 100% 100%, 0 100%);
}

.hide-toggle-btn {
  margin-left: 10px;
  background: transparent;
  border: none;
  cursor: pointer;
  outline: none;
}

.navbar-list-droptoggle {
  position: fixed;
  left: -20%;
  background: #fff;
  min-height: 100vh;
  width: 80%;
  padding-top: 10px;
  color: #000;
  clip-path: polygon(0 0, 0 2%, 0 100%, 0 100%);
  transition: 0.4s ease;
}

.navbar-list-droptoggle.active {
  clip-path: polygon(100% 0, 0 1%, 0 100%, 100% 100%);
}

.navbar-list-droptoggle i {
  color: #000;
}

.navbar-list-droptoggle ul {
  list-style-type: none;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.navbar-list-droptoggle ul li {
  margin: 15px 0;
}

.navbar-list-droptoggle ul li:hover {
  text-decoration: underline;
}

span {
  cursor: pointer;
}

a {
  cursor: pointer !important;
}

@media screen and (max-width: 400px) {
  .navbar-list-droptoggle {
    width: 100%;
    left: 0;
  }
}
</style>
