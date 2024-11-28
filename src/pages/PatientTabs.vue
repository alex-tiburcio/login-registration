<template>
  <div class="main-login-bg ">
    <div class="top-mobile">
      <img src="~assets/myhhub_logo_v2.svg" alt="MyHhub" class="rounded logo-main" />
    </div>
    <div class="flex login-left-section" style="height: 100vh;">
      <img src="~assets/myhhub_logo_v2.svg" alt="MyHhub" class="rounded logo-main" />
    </div>
    <div class="flex login-right-section" style="height: 100vh;">
      <div v-if="isPatient" class="">
        <div class="text-h6 login-title-section">Existing Patient</div>
        <p>Login to start your session</p>
        <div class="login-form-login">
          <q-form @submit="handleSubmit" dark class="q-gutter-md register-form">
            <q-input dark v-model="email" label="Email/Phone" outlined type="email" color="white"
              class="q-mb-sm  text-white custom-placeholder" :rules="[val => !!val || 'Email/Phone is required']">
              <template v-slot:append>
                <q-icon name="fas fa-user" class="text-white" />
              </template>
            </q-input>
            <q-input dark v-model="password" label="Password" type="password" outlined color="white"
              class="q-mb-sm q-mt-xl text-white " :rules="[val => !!val || 'Password is required']">
              <template v-slot:append>
                <q-icon name="fas fa-lock" class="text-white" />
              </template>
            </q-input>
          </q-form>
        </div>

        <div class="login-buttons">
          <q-btn class="main-button-login" label="Login" size="18px" color="white" text-color="blue-9" type="submit" />
          <div class="text-left content-links-login">
            <q-btn label="Reset password" flat color="white" />
          </div>
          <div class="text-right content-links-login">
            <q-btn label="Login with code" flat color="white" />
          </div>
        </div>
        <div class="loggin-toggle-container">
          <p class=""> Don´t have an account? Please click on the next toggle to be moved to New patient section for
            register.
          </p>
          <span class="q-mr-sm">New patient</span>
          <q-toggle v-model="isPatient" checked-icon="fa solid fa-user-check" color="amber-5"
            unchecked-icon="fa regular fa-user-plus" size="lg" track-color="light-green-7"
            thumb-color="light-green-7" />
          <span class="q-mr-sm">Existing patient</span>
        </div>
      </div>

      <div v-else class="">
        <div class="text-h6 login-title-section">New patient</div>

        <div class="q-pa-md">
          <div class="login-subtitle">Who is the appointment for?</div>
          <q-option-group dark :options="options" type="radio" v-model="selectedOption" />

          <div class="bg-red-2 text-red-9 login-error-message" v-if="showErrorMessage">
            We are sorry.
            You only can make an appointment for yourself.
          </div>

          <div class="login-buttons">
            <q-btn label="Next" class="main-button-login" size="18px" color="white" text-color="blue-9"
              @click="nextStep()" />
          </div>
        </div>

        <div class="loggin-toggle-container">
          <p class=""> Do you have an account? Please click on the next toggle to be moved to Existing patient for
            login.
          </p>
          <span class="q-mr-sm">New Patient</span>
          <q-toggle v-model="isPatient" checked-icon="fa solid fa-user-check" color="amber-5"
            unchecked-icon="fa regular fa-user-plus" size="lg" track-color="light-green-7"
            thumb-color="light-green-7" />
          <span class="q-mr-sm">Existing patient</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email:"",
      password:"",
      isPatient:true,
      selectedOption: "",
      options: [
        { label: 'For me', value: 'me', color: 'white' },
        { label: 'For my child', value: 'child', color: 'white' },
        { label: 'For someone else', value: 'else', color: 'white' }
      ],
      showErrorMessage: false,
    };
  },
  methods: {
    handleSubmit(){
    },

    nextStep(){
      if(this.selectedOption == "me"){
        this.$router.push("registration");
      }else{
        this.showErrorMessage = true;
      }
    }
  },
  computed: {
    labelToggle(){
      return this.isPatient ? 'Existing patient' : 'New patient';
    }
  },
  watch:{
    selectedOption: function (val) {
      this.showErrorMessage = false;
    },
  }
};
</script>

