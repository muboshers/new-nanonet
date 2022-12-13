<template>
  <div>
    <Header />
    <PageTitle :pageTitle="category ? category.title : ''" />
    <About />

    <div class="data-container" v-if="eduData.length > 0">
      <h2 class="text-center">{{ $t("header.service") }}</h2>
      <div class="service-area bg-color area-padding-2">
        <div class="container">
          <div class="row">
            <div class="all-services">
              <div
                class="col-md-4 col-sm-6 col-xs-12"
                v-for="(service, index) of eduData"
                :key="index"
              >
                <div class="single-service wow fadeInUp" data-wow-delay="0.3s">
                  <div class="service-inner">
                    <div class="service-content">
                      <h4>{{ service.title }}</h4>
                      <p>
                        {{ service.description }}
                      </p>
                      <div class="main-service-info">
                        <span>{{ service.online ? "online" : "offline" }}</span>
                        <span>{{ dateFormat(service.startDate) }}</span>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <Welcome />
    <div v-if="serviceData.length > 0">
      <div class="service-area bg-color area-padding-2">
        <div class="container">
          <div class="row">
            <div class="all-services">
              <div
                class="col-md-4 col-sm-6 col-xs-12"
                v-for="(service, index) of serviceData"
                :key="index"
              >
                <div class="single-service wow fadeInUp" data-wow-delay="0.3s">
                  <div class="service-inner">
                    <div class="service-content">
                      <h4>{{ service.title }}</h4>
                      <p>
                        {{ service.description }}
                      </p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <Quote />
    <Footer />
  </div>
</template>

<script>
import Header from "../../components/Header";
import Quote from "../../components/Quote";
import Welcome from "../../components/Welcome";
import PageTitle from "../../components/PageTitle";
import About from "../../components/About";
import Footer from "../../components/Footer";

export default {
  components: {
    Header,
    PageTitle,
    Welcome,
    Quote,
    About,
    Footer
  },
  data() {
    return {
      category: null,
      serviceData: [],
      eduData: []
    };
  },
  head() {
    title: "Single Service";
  },

  methods: {
    async getCategoryById() {
      const { id } = this.$route.params;
      await fetch(
        `https://consultingweb.duckdns.org/api/v1/category/${id}?lang=${this.$t(
          "requestLanguage"
        )}`
      )
        .then(res => res.json())
        .then(d => (this.category = d.data))
        .catch(err => console.log(err.message));
    },
    async getAllService(url, data) {
      const { id } = this.$route.params;
      await fetch(`${url}?lang=${this.$t("requestLanguage")}&categoryId=${id}`)
        .then(res => res.json())
        .then(d => (this[data] = d.data))
        .catch(err => console.log(err));
    },
    dateFormat(date) {
      const newTime = new Date(date);
      return `${newTime.getDate()}/${newTime.getMonth() + 1}`;
    }
  },
  mounted() {
    this.getCategoryById();
    this.getAllService(
      "https://consultingweb.duckdns.org/api/v1/service/list",
      "serviceData"
    );
    this.getAllService(
      "https://consultingweb.duckdns.org/api/v1/service/edu/list",
      "eduData"
    );
  }
};
</script>

<style scoped>
.main-service-info {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.data-container {
  background-color: rgb(245, 248, 251);
  padding: 2rem 0;
}
</style>
