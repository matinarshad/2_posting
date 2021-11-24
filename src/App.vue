<template>
  <div class="col-lg-8 mx-auto p-3 py-md-5">
    <header class="d-flex align-items-center pb-3 mb-5 border-bottom">
      <a
        href="/"
        class="d-flex align-items-center text-dark text-decoration-none"
      >
        <span class="fs-4">📚 SingleView Task 2: Posting</span>
      </a>
    </header>

    <main>
      <h1>Speak with us!</h1>
      <p class="fs-5">
        Below is a simple form. Data input in this form should be submitted to
        <u>https://httpbin.org/post</u>
      </p>
      <br />

      <div class="row g-5">
        <div class="col-md-5 col-lg-4 order-md-last">
          <h4 class="d-flex justify-content-between align-items-center mb-3">
            <span class="text-primary">Your membership</span>
            <span class="badge bg-primary rounded-pill">3</span>
          </h4>
          <ul class="list-group mb-3">
            <li class="list-group-item d-flex justify-content-between lh-sm">
              <div>
                <h6 class="my-0">Platform Access</h6>
                <small class="text-muted">1 year access</small>
              </div>
              <span class="text-muted">£100</span>
            </li>
            <li class="list-group-item d-flex justify-content-between lh-sm">
              <div>
                <h6 class="my-0">Weekly exploration session</h6>
                <small class="text-muted"
                  >Online 1-1 session with team member</small
                >
              </div>
              <span class="text-muted">£15</span>
            </li>
            <li class="list-group-item d-flex justify-content-between bg-light">
              <div class="text-success">
                <h6 class="my-0">Onboarding session</h6>
                <small>In depth platform session</small>
              </div>
              <span class="text-success">£0</span>
            </li>
            <li class="list-group-item d-flex justify-content-between">
              <span>Total (GBP)</span>
              <strong>£115</strong>
            </li>
          </ul>
        </div>
        <div class="col-md-7 col-lg-8">
          <h4 class="mb-3">Contact Information</h4>
          <form
            class="needs-validation"
            novalidate=""
            v-on:submit.prevent="onSubmit"
          >
            <div class="row g-3">
              <div class="col-sm-6">
                <label for="firstName" class="form-label">First name</label>
                <input
                  v-model="first_name"
                  type="text"
                  class="form-control"
                  id="firstName"
                  placeholder=""
                  required=""
                />
              </div>

              <div class="col-sm-6">
                <label for="lastName" class="form-label">Last name</label>
                <input
                  v-model="last_name"
                  type="text"
                  class="form-control"
                  id="lastName"
                  placeholder=""
                  required=""
                />
              </div>

              <div class="col-12">
                <label for="email" class="form-label"
                  >Email <span class="text-muted"></span
                ></label>
                <input
                  v-model="email"
                  type="email"
                  class="form-control"
                  id="email"
                  placeholder="you@example.com"
                />
              </div>

              <div class="col-12">
                <label for="mobile" class="form-label"
                  >Mobile <span class="text-muted"></span
                ></label>
                <input
                  v-model="mobile"
                  type="mobile"
                  class="form-control"
                  id="Mobile"
                  placeholder="07777 777777"
                />
              </div>
            </div>

            <hr class="my-4" />

            <div class="form-check">
              <input
                v-model="allow_mobile"
                type="checkbox"
                class="form-check-input"
                id="allow-mobile"
              />
              <label class="form-check-label" for="same-address"
                >I'm happy to be contacted via mobile</label
              >
            </div>

            <hr class="my-4" />

            <button
              class="w-100 btn btn-primary btn-lg"
              type="submit"
              @click="send"
            >
              Get in touch
            </button>
          </form>
        </div>
      </div>
    </main>
    <footer class="pt-5 my-5 text-muted border-top">SingleView</footer>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "App",
  data() {
    return {
      first_name: "",
      last_name: "",
      email: "",
      mobile: "",
      allow_mobile: false,
    };
  },
  methods: {
    send(e) {
      e.prevent;

      var data2 = JSON.stringify({
        first_name: this.first_name,
        last_name: this.last_name,
        email: this.email,
        mobile: this.mobile,
        allow_mobile: this.allow_mobile,
      });

      var config = {
        method: "post",
        url: "https://httpbin.org/post",
        headers: {
          "Content-Type": "application/json",
        },
        data: data2,
      };

      axios(config)
        .then(function (response) {
          console.log(JSON.stringify(response.data));
        })
        .catch(function (error) {
          console.log(error);
        });
    },
  },
};
</script>

<style>
@import "~bootstrap/dist/css/bootstrap.css";
</style>
