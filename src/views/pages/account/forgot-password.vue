<script>
import appConfig from "@/app.config";

import { required, email } from "@vuelidate/validators";
import useVuelidate from "@vuelidate/core";

/**
 * Forgot Password component
 */
export default {
  page: {
    title: "Forgot Password",
    meta: [
      {
        name: "description",
        content: appConfig.description,
      },
    ],
  },
  setup() {
    return {
      v$: useVuelidate()
    };
  },
  data() {
    return {
      email: "",
      submitted: false,
      error: null,
      title: "Recoverpwd",
    };
  },
  validations: {
    email: {
      required,
      email,
    },
  },
  methods: {
    // Try to register the user in with the email, fullname
    // and password they provided.
    tryToReset() {
      this.submitted = true;
      // stop here if form is invalid
      this.v$.$touch();

      if (this.v$.$invalid) {
        return;
      } else {
        if (process.env.VUE_APP_DEFAULT_AUTH === "firebase") {
          this.tryingToReset = true;
          // Reset the authError if it existed.
          this.error = null;
          return (
            this.$store
              .dispatch("auth/resetPassword", {
                email: this.email,
              })
              .then((token) => {
                console.log("token", token);
                this.tryingToReset = false;
                this.isResetError = false;
              })
              .catch((error) => {
                this.tryingToReset = false;
                this.error = error ? error : "";
                this.isResetError = true;
              })
          );
        }
      }
    },
  },
};
</script>

<template>
  <div>
    <div class="account-pages my-5 pt-sm-5">
      <BContainer>
        <BRow class="justify-content-center">
          <BCol md="8" lg="6" xl="5">
            <div>
              <router-link to="/" class="mb-5 d-block auth-logo">
                <img src="@/assets/images/logo-dark.png" alt height="22" class="logo logo-dark" />
                <img src="@/assets/images/logo-light.png" alt height="22" class="logo logo-light" />
              </router-link>
              <BCard no-body>
                <BCardBody class="p-4">
                  <div class="text-center mt-2">
                    <h5 class="text-primary">Reset Password</h5>
                    <p class="text-muted">Reset Password with Minible.</p>
                  </div>
                  <div class="p-2 mt-4">
                    <div class="alert alert-success text-center mb-4" role="alert">
                      Enter your Email and instructions will be sent to you!
                    </div>
                    <BForm @submit.prevent="tryToReset">
                      <div class="mb-3">
                        <label for="useremail">Email</label>
                        <input type="email" v-model="email" class="form-control" id="useremail" placeholder="Enter email" :class="{
                          'is-invalid': submitted && v$.email.$error,
                        }" />
                        <div v-if="submitted && v$.email.$error" class="invalid-feedback">
                          <span v-if="!v$.email.required">Email is required.</span>
                          <span v-if="!v$.email.email">Please enter valid email.</span>
                        </div>
                      </div>
                      <BRow class="mb-0">
                        <BCol cols="12" class="text-end">
                          <BButton variant="primary" class="w-sm" type="submit">
                            Reset
                          </BButton>
                        </BCol>
                      </BRow>
                      <div class="mt-4 text-center">
                        <p class="mb-0">
                          Remember It ?
                          <router-link to="/login" class="fw-medium text-primary">Signin</router-link>
                        </p>
                      </div>
                    </BForm>
                  </div>
                </BCardBody>
              </BCard>

              <div class="mt-5 text-center">
                <p>
                  © {{ new Date().getFullYear() }} Minible. Crafted with
                  <i class="mdi mdi-heart text-danger"></i> by Themesbrand
                </p>
              </div>
            </div>
          </BCol>
        </BRow>
      </BContainer>
    </div>
  </div>
</template>

<style lang="scss" module></style>
