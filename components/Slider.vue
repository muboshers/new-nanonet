<template>
  <div class="intro-area-2">
    <div class="intro-carousel">
      <div
        class="intro-content-2"
        v-for="(slide, index) in $t('home.slide.content')"
        :key="index"
      >
        <div class="slider-images">
          <img :src="`/img/slider/h${index + 1}.jpg`" alt="" />
        </div>
        <div class="slider-content">
          <div class="display-table">
            <div class="display-table-cell">
              <div class="container">
                <div class="row">
                  <div class="col-md-12">
                    <div class="layer-1 wow fadeInUp" data-wow-delay="0.3s">
                      <h2 class="title2">
                        {{ slide.title }}
                      </h2>
                    </div>
                    <div class="layer-2 wow fadeInUp" data-wow-delay="0.5s">
                      <p>
                        {{ slide.description }}
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
  </div>
</template>

<script>
export default {
  name: "Slider",
  mounted() {
    var intro_carousel = $(".intro-carousel");
    intro_carousel.owlCarousel({
      loop: true,
      nav: true,
      autoplay: false,
      dots: false,
      navText: [
        "<i class='ti-angle-left'></i>",
        "<i class='ti-angle-right'></i>"
      ],
      responsive: {
        0: {
          items: 1
        },
        600: {
          items: 1
        },
        1000: {
          items: 1
        }
      }
    });
  }
};
</script>

<style scoped></style>
