<template>
  <div class="reviews-area area-padding">
    <div class="container">
      <div class="row">
        <div class="col-md-12 col-sm-12 col-xs-12">
          <div class="section-headline text-center">
            <h3>Customer say some words</h3>
            <p>
              Help agencies to define their new business objectives and then
              create professional software.
            </p>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-md-12 col-sm-12 col-xs-12">
          <div class="Reviews-content">
            <div class="testimonial-carousel item-indicator">
              <div class="single-testi" v-for="(about, index) in data">
                <div class="testi-text">
                  <div class="clients-text">
                    <p>
                      {{ about.description }}
                    </p>
                    <div class="testi-img ">
                      <div class="guest-details">
                        <h4>{{ about.title }}</h4>
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
  </div>
</template>

<script>
export default {
  name: "Reviews",

  data() {
    return {
      data: null
    };
  },
  methods: {
    aboutInfo() {
      this.aboutUsRequest()
        .then(res => res.json())
        .then(d => {
          this.data = d.data;
        })
        .catch(err => console.log(err));
    },
    async aboutUsRequest() {
      return await fetch(
        `https://consultingweb.duckdns.org/api/v1/about-us?lang=${this.$t(
          "requestLanguage"
        )}`
      );
    }
  },
  beforeMount() {
    this.aboutInfo();
  },
  mounted() {
    setTimeout(() => {
      var review = $(".testimonial-carousel");
      review.owlCarousel({
        loop: true,
        nav: false,
        margin: 15,
        center: true,
        dots: true,
        autoplay: false,
        responsive: {
          0: {
            items: 1
          },
          768: {
            items: 2
          },
          1000: {
            items: 3
          }
        }
      });
    }, 2000);
  }
};
</script>

<style scoped></style>
