<script>
import { required, email } from "@vuelidate/validators";
import useVuelidate from "@vuelidate/core";
import appConfig from "@/app.config";

/**
 * Login component
 */
export default {
  setup() {
    return {
      v$: useVuelidate()
    };
  },
  page: {
    title: "Login",
    meta: [
      {
        name: "description",
        content: appConfig.description,
      },
    ],
  },
  data() {
    return {
      email: "admin@themesbrand.com",
      password: "123456",
      submitted: false,
      authError: null,
      tryingToLogIn: false,
      isAuthError: false,
    };
  },
  validations: {
    email: {
      required,
      email,
    },
    password: {
      required,
    },
  },
  computed: {
    notification() {
      return this.$store ? this.$store.state.notification : null;
    },
    notificationAutoCloseDuration() {
      return this.$store && this.$store.state.notification ? 5 : 0;
    },
  },
  mounted() {
    document.body.classList.add("authentication-bg");
  },
  methods: {
    // Try to log the user in with the username
    // and password they provided.
    tryToLogIn() {
      this.submitted = true;
      // stop here if form is invalid
      this.v$.$touch();

      if (this.v$.$invalid) {
        return;
      } else {
        if (process.env.VUE_APP_DEFAULT_AUTH === "firebase") {
          this.tryingToLogIn = true;
          // Reset the authError if it existed.
          this.authError = null;
          return (
            this.$store
              .dispatch("auth/logIn", {
                email: this.email,
                password: this.password,
              })
              .then((token) => {
                console.log("token", token);
                this.tryingToLogIn = false;
                this.isAuthError = false;
                // Redirect to the originally requested page, or to the home page
                this.$router.push(
                  this.$route.query.redirectFrom || {
                    path: "/",
                  }
                );
              })
              .catch((error) => {
                this.tryingToLogIn = false;
                this.authError = error ? error : "";
                this.isAuthError = true;
              })
          );
        } else if (process.env.VUE_APP_DEFAULT_AUTH === "fakebackend") {
          const { email, password } = this;
          if (email && password) {
            this.$store.dispatch("authfack/login", {
              email,
              password,
            });
          }
        }
      }
    },
  },
};
</script>

<template>
  <div class="login-container">
    <!-- Split Background Layout -->
    <div class="split-layout">
      <!-- Left Blue Section -->
      <div class="left-section"></div>
      
      <!-- Right Light Section -->
      <div class="right-section"></div>
    </div>
    
    <!--  Moved login card outside split sections to center it across both -->
    <!-- Centered Login Card Container -->
    <div class="login-card-overlay">
      <div class="login-card-container">
        <BCard no-body class="login-card">
          <BCardBody class="p-5">
            <!-- AB Bank Logo and Branding -->
            <div class="text-center mb-4">
              <div class="logo-container mb-3">
                <img src="@/assets/images/nova-logo.png" alt height="42" />
              </div>
              <h4 class="portal-title mb-4">Nova Bank NPS Portal</h4>
              <p class="login-subtitle">Login with your company domain email</p>
            </div>

            <!-- Login Form -->
            <BForm @submit.prevent="tryToLogIn">
              <BAlert v-model="isAuthError" variant="danger" class="mt-3" dismissible>{{ authError }}</BAlert>

              <div v-if="notification && notification.message" :class="'alert alert-' + notification.type">
                {{ notification.message }}
              </div>

              <!-- Email Field -->
              <BFormGroup class="mb-3">
                <BFormInput 
                  v-model="email" 
                  type="email" 
                  placeholder="Email" 
                  class="form-input"
                  :class="{ 'is-invalid': submitted && v$.email.$error }"
                ></BFormInput>
                <div v-if="submitted && v$.email.$error" class="invalid-feedback">
                  <span v-if="!v$.email.required">Email is required.</span>
                  <span v-if="!v$.email.email">Please enter valid email.</span>
                </div>
              </BFormGroup>

              <!-- Password Field -->
              <BFormGroup class="mb-3">
                <label class="form-label">Password</label>
                <div class="password-input-container">
                  <!-- <BFormInput 
                    v-model="password" 
                    type="password" 
                    placeholder="Enter password" 
                    class="form-input"
                    :class="{ 'is-invalid': submitted && v$.password.$error }"
                  ></BFormInput>
                  <button type="button" class="password-toggle">
                    <i class="fas fa-eye"></i>
                  </button> -->

                   <BFormInput 
  v-model="password" 
  :type="text" 
  placeholder="Enter password" 
  class="form-input"
  :class="{ 'is-invalid': submitted && v$.password.$error }"
/>
<button 
  type="button" 
  class="password-toggle" 
  @click="togglePasswordVisibility"
>
  <i :class="showPassword ? 'fas fa-eye-slash' : 'fas fa-eye'"></i>
</button>
                </div>
                <div v-if="submitted && !v$.password.required" class="invalid-feedback">
                  Password is required.
                </div>
              </BFormGroup>

              <!-- Remember Me and Forgot Password -->
              <div class="form-options mb-4">
                <div class="form-check">
                  <input type="checkbox" class="form-check-input" id="remember-me" />
                  <label class="form-check-label" for="remember-me">Remember me</label>
                </div>
                <router-link to="/forgot-password" class="forgot-password">Forgot password?</router-link>
              </div>

              <!-- Sign In Button -->
              <BButton type="submit" class="sign-in-btn w-100" :disabled="tryingToLogIn">
                {{ tryingToLogIn ? 'Signing in...' : 'Sign in' }}
              </BButton>
            </BForm>
          </BCardBody>
        </BCard>
      </div>
    </div>
  </div>
</template>

<style scoped>
.login-container {
  min-height: 100vh;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  position: relative;
}

.split-layout {
  display: flex;
  min-height: 100vh;
  position: absolute;
  width: 100%;
  top: 0;
  left: 0;
}

.left-section {
  flex: 1;
  background: linear-gradient(135deg, #1e88e5 0%, #1565c0 100%);
  position: relative;
}

.left-section::before {
  content: '';
  position: absolute;
  bottom: 0;
  right: 0;
  width: 200px;
  height: 200px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 50% 0 0 0;
}

.right-section {
  flex: 1;
  background: #f8f9fa;
}

/*  Added overlay positioning to center login card across both sections */
.login-card-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
  z-index: 10;
}

.login-card-container {
  width: 100%;
  max-width: 400px;
}

.login-card {
  border: none;
  border-radius: 12px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  background: white;
}

.logo-container {
  display: flex;
  align-items: center;
  justify-content: center;
  object-fit: cover;
}

.logo-circle {
  width: 40px;
  height: 40px;
  background: #1e88e5;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.logo-text {
  color: white;
  font-weight: bold;
  font-size: 16px;
}

.bank-name {
  text-align: left;
  line-height: 1.2;
}

.bank-main {
  font-weight: 600;
  font-size: 14px;
  color: #333;
}

.bank-sub {
  font-weight: 600;
  font-size: 14px;
  color: #333;
}

.portal-title {
  font-size: 24px;
  font-weight: 600;
  color: #333;
  margin: 0;
}

.login-subtitle {
  color: #666;
  font-size: 14px;
  margin: 0;
}

.form-label {
  font-size: 14px;
  font-weight: 500;
  color: #333;
  margin-bottom: 8px;
  display: block;
}

.form-input {
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  padding: 12px 16px;
  font-size: 14px;
  background: #f8f9fa;
  transition: all 0.2s ease;
}

.form-input:focus {
  border-color: #1e88e5;
  box-shadow: 0 0 0 3px rgba(30, 136, 229, 0.1);
  background: white;
}

.form-input::placeholder {
  color: #999;
}

.password-input-container {
  position: relative;
}

.password-toggle {
  position: absolute;
  right: 12px;
  top: 50%;
  transform: translateY(-50%);
  background: none;
  border: none;
  color: #999;
  cursor: pointer;
  padding: 4px;
}

.form-options {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.form-check {
  display: flex;
  align-items: center;
  gap: 8px;
}

.form-check-input {
  margin: 0;
}

.form-check-label {
  font-size: 14px;
  color: #666;
  margin: 0;
  cursor: pointer;
}

.forgot-password {
  color: #1e88e5;
  text-decoration: none;
  font-size: 14px;
}

.forgot-password:hover {
  text-decoration: underline;
}

.sign-in-btn {
  background: #1e88e5;
  border: none;
  border-radius: 8px;
  padding: 12px;
  font-size: 16px;
  font-weight: 600;
  transition: background-color 0.2s ease;
}

.sign-in-btn:hover:not(:disabled) {
  background: #1565c0;
}

.sign-in-btn:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

/* Responsive Design */
@media (max-width: 768px) {
  .split-layout {
    flex-direction: column;
  }
  
  .left-section {
    min-height: 200px;
    flex: none;
  }
  
  .right-section {
    flex: 1;
    padding: 1rem;
  }
  
  .login-card-container {
    max-width: 100%;
  }
}
</style>