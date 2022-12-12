<template>
  <div class="about-area about-2 fix">
    <div class="container-full">
      <div class="row">
        <div class="col-md-5 col-sm-4 col-xs-12">
          <div class="about-image" style="min-height: inherit;"></div>
        </div>
        <div class="col-md-7 col-sm-8 col-xs-12">
          <div class="support-all about-content">
            <div class="section-headline right-headline white-headline">
              <h3>
                {{ $t("about.title") }}
              </h3>
              <p>
                {{ $t("about.description") }}
              </p>
            </div>
            <div class="about-company">
              <div
                class="single-about"
                v-for="(singleAbout, index) in $t('about.singleAbout')"
                :key="index"
              >
                <span
                  class="about-text"
                  v-for="(aboutItem, index) in singleAbout"
                  :key="index"
                  >{{ aboutItem }}</span
                >
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
  name: "About",
  mounted() {
    $(".video-play").magnificPopup({
      type: "iframe"
    });
  }
};
</script>

<style scoped></style>
