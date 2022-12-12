<template>
  <div class="service-area bg-color area-padding-2">
    <div class="container">
      <div class="row">
        <div class="col-md-12 col-sm-12 col-xs-12">
          <div class="section-headline text-center">
            <h3>{{ $t("service.title") }}</h3>
            <p>
              {{ $t("service.description") }}
            </p>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="all-services">
          <div
            v-if="data.length > 0"
            class="col-md-4 col-sm-6 col-xs-12"
            v-for="(service, index) of data"
            :key="index"
          >
            <div class="single-service wow fadeInUp" data-wow-delay="0.3s">
              <div class="service-inner">
                <div class="service-content">
                  <h4>{{ service.title }}</h4>
                  <p>
                    {{ service.description.slice(0, 100) + "..." }}
                  </p>

                  <nuxt-link :to="localePath(`/services/${service.id}`)">
                    <button class="btn">{{ $t("read") }}</button>
                  </nuxt-link>
                </div>
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
  name: "Service",
  data() {
    return {
      data: []
    };
  },
  methods: {
    async getCategoryInformation() {
      await fetch(
        `https://consultingweb.duckdns.org/api/v1/category/list?lang=${this.$t(
          "requestLanguage"
        )}`
      )
        .then(res => res.json())
        .then(d => (this.data = d.data))
        .catch(err => console.log(err.message));
    }
  },

  mounted() {
    this.getCategoryInformation();
  }
};
</script>

<style scoped></style>
