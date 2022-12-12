<template>
  <div class="welcome-area fix area-padding">
    <div class="container">
      <div class="row">
        <div class="col-md-12 col-sm-12 col-xs-12">
          <div class="all-wel-services">
            <div
              class="well-services wow fadeInUp"
              v-for="(welcomeCard, index) of $t('welcomeCard')"
              :key="index"
              data-wow-delay="0.3s"
            >
              <div class="services-img">
                <a class="big-icon" href="#"
                  ><i class="flaticon-052-project-plan"></i
                ></a>
              </div>
              <div class="main-wel">
                <div class="wel-content">
                  <h4>{{ welcomeCard.title }}</h4>
                  <p>
                    {{ welcomeCard.description }}
                  </p>
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
  name: "Welcome"
};
</script>

<style scoped></style>
