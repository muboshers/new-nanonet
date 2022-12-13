<template>
  <div class="quote-area bg-color area-padding">
    <div class="container">
      <div class="row">
        <div class="col-md-12 col-sm-12">
          <div class="row">
            <div class="col-md-5 col-sm-4 col-xs-12">
              <div class="sub-head white-headline">
                <h3>{{ $t("contact.title") }}</h3>
                <p>
                  {{ $t("contact.description") }}
                </p>
              </div>
            </div>
            <div class="col-md-7 col-sm-8 col-xs-12">
              <div class="row">
                <form id="contactForm" @submit.prevent class="contact-form">
                  <div class="col-md-6 col-sm-6 col-xs-12">
                    <input
                      type="text"
                      v-model="fullName"
                      class="form-control input"
                      :placeholder="$t('contact.name')"
                    />
                    <div class="help-block with-errors"></div>
                    <input
                      type="email"
                      v-model="email"
                      class="email form-control input"
                      :placeholder="$t('contact.email')"
                    />
                    <div class="help-block with-errors"></div>
                    <input
                      type="text"
                      v-model="phoneNumber"
                      class="form-control last-part input"
                      :placeholder="$t('contact.phoneNumber')"
                    />
                    <div class="help-block with-errors last-part"></div>
                  </div>
                  <div class="col-md-6 col-sm-6 col-xs-12">
                    <textarea
                      type="text"
                      class="form-control"
                      :placeholder="$t('contact.message')"
                      v-model="description"
                    />
                    <div class="help-block with-errors"></div>
                    <button
                      type="submit"
                      id="submit"
                      @click="createContactMessage"
                      class="quote-btn"
                    >
                      {{ $t("contact.button") }}
                    </button>
                    <div id="msgSubmit" class="h3 text-center hidden"></div>
                    <div class="clearfix"></div>
                  </div>
                </form>
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
  name: "Quote",
  data() {
    return {
      fullName: "",
      description: "",
      phoneNumber: "",
      email: "",
    };
  },
  methods: {
    async contactMessageRequest() {
      return await fetch(
        "https://consultingweb.duckdns.org/api/v1/application/create",
        {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify({
            fullName: this.fullName,
            description: this.description,
            phoneNumber: this.phoneNumber,
            email: this.email,
            subject: "",
          }),
        }
      );
    },

    createContactMessage() {
      this.contactMessageRequest()
        .then((res) => res.json())
        .then((d) => console.log(d))
        .catch((err) => console.log(err));

      this.fullName = "";
      this.description = "";
      this.phoneNumber = "";
      this.email = "";
    },
  },
};
</script>

<style scoped>
textarea {
  border: none;
  outline: none;
  height: 200px;
  margin-bottom: 20px;
  border: 1px solid rgba(49, 120, 251, 0.4);
  border-radius: 3px;
  color: #fff;
  background-color: transparent;
}

.form-control:focus {
  border-color: rgba(49, 120, 251, 0.4);
}

@media screen and (max-width: 768px) {
  input,
  textarea {
    width: 100% !important;
  }
}
</style>
