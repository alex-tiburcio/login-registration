<template>
  <div class="main-registration-bg">
    <div class="top-mobile">
      <img src="~assets/myhhub_logo_v2.svg" alt="MyHhub" class="rounded logo-main" />
    </div>
    <div class="flex register-left-section" style="height: 100vh;">
      <div class="register-form-container">
        <div class="text-h6 login-title-section">Register</div>
        <p>Please fill with your information</p>
        <q-form @submit="handleSubmit" dark class="q-gutter-md register-form">

          <div class="row register-row-form">
            <div class="col-12 col-md-6">
              <q-input dark dense outlined color="white" class="q-mb-sm  text-white custom-placeholder" label="First Name"
                v-model="form.firstName" required :rules="[val => !!val || 'First name is required']">
                <template v-slot:append>
                  <q-icon name="fas fa-user" class="text-white" />
                </template>
              </q-input>
            </div>
            <div class="col-12 col-md-6 ">

              <q-input dense dark outlined color="white" class="q-mb-sm  text-white custom-placeholder" label="Middle Name"
                v-model="form.middleName" :rules="[val => !!val || 'Middle name is required']">
                <template v-slot:append>
                  <q-icon name="fas fa-user" class="text-white" />
                </template>
              </q-input>
            </div>
          </div>

          <div class="row register-row-form">
            <div class="col-12 col-md-6">
              <q-input dense dark outlined color="white" class="q-mb-sm  text-white custom-placeholder" label="Last Name"
                v-model="form.lastName" required :rules="[val => !!val || 'Last name is required']"> 
                <template v-slot:append>
                  <q-icon name="fas fa-user" class="text-white" />
                </template>
              </q-input>
            </div>

            <div class="col-12 col-md-6">
              <q-input  dense dark outlined color="white" v-model="form.dob" mask="date" :rules="['date']"
                placeholder="Date of Birth" >
                <template v-slot:append>
                  <q-icon name="event" class="cursor-pointer">
                    <q-popup-proxy cover transition-show="scale" transition-hide="scale">
                      <q-date v-model="form.dob">
                        <div class="row items-center justify-end">
                          <q-btn v-close-popup label="Close" color="primary" flat />
                        </div>
                      </q-date>
                    </q-popup-proxy>
                  </q-icon>
                </template>
              </q-input>
            </div>
          </div>

          <div class="row register-row-form">
            <div class="col-12 col-md-4">
              <q-input  dense dark outlined color="white" class="q-mb-sm  text-white custom-placeholder"
                label="SSN (Last 4 Digits)" v-model="form.ssn" type="number" maxlength="4" required :rules="[val => !!val || 'SSN is required']"> <template
                  v-slot:append>
                  <q-icon name="fas fa-hashtag" class="text-white" />
                </template>
              </q-input>
            </div>

            <div class="col-12 col-md-4">
              <q-input  dense dark outlined color="white" class="q-mb-sm  text-white custom-placeholder" label="Phone Number"
                v-model="form.phone" mask="(###) ###-####" type="tel" required :rules="[val => !!val || 'Phone number is required']"> <template v-slot:append>
                  <q-icon name="fas fa-phone" class="text-white" />
                </template>
              </q-input>
            </div>

            <div class="col-12 col-md-4">
              <q-input dense dark outlined color="white" class="q-mb-sm  text-white custom-placeholder" label="Email"
                v-model="form.email" type="email" required :rules="[val => !!val || 'Email is required']"> <template v-slot:append>
                  <q-icon name="fas fa-envelope" class="text-white" />
                </template>
              </q-input>
            </div>

          </div>
          <div class="row register-row-form">
            <div class="col-12 col-md-6">

              <q-input dense dark outlined color="white" class="q-mb-sm  text-white custom-placeholder" label="Street Name"
                v-model="form.street" required :rules="[val => !!val || 'Street is required']"> <template v-slot:append>
                  <q-icon name="fas fa-house" class="text-white" />
                </template>
              </q-input>
            </div>

            <div class="col-12 col-md-6">

              <q-input dense dark outlined color="white" class="q-mb-sm  text-white custom-placeholder" label="Suite/Apt"
                v-model="form.suite" :rules="[val => !!val || 'Suite/Apt is required']"> <template v-slot:append>
                  <q-icon name="fas fa-house" class="text-white" />
                </template>
              </q-input>
            </div>
          </div>
          <div class="row register-row-form">
            <div class="col-12 col-md-6">

              <q-input dense dark outlined color="white" class="q-mb-sm  text-white custom-placeholder" label="City"
                v-model="form.city" required :rules="[val => !!val || 'City  is required']"> <template v-slot:append>
                  <q-icon name="fas fa-house" class="text-white" />
                </template>
              </q-input>
            </div>

            <div class="col-12 col-md-6">

              <q-input dense dark outlined color="white" class="q-mb-sm  text-white custom-placeholder" label="State/Province"
                v-model="form.state" required :rules="[val => !!val || 'State/Province  is required']"> <template v-slot:append>
                  <q-icon name="fas fa-house" class="text-white" />
                </template>
              </q-input>
            </div>
          </div>
          <div class="row register-row-form">
            <div class="col-12 col-md-6">

              <q-select dense dark outlined color="white" class="q-mb-sm  text-white custom-placeholder" label="Country"
                v-model="form.country" :options="countries" emit-value map-options required :rules="[val => !!val || 'Country is required']"> <template v-slot:append>
                  <q-icon name="fas fa-house" class="text-white" />
                </template>
              </q-select>
            </div>

            <div class="col-12 col-md-6">

              <q-input dense dark outlined color="white" class="q-mb-sm  text-white custom-placeholder"
                label="Zip/Postal Code" v-model="form.zip" type="number" required :rules="[val => !!val || 'Zip/Postal Code is required']">
                <template v-slot:append>
                  <q-icon name="fas fa-house" class="text-white" />
                </template>
              </q-input>
            </div>
          </div>
          <div class="login-buttons">

            <div class="text-left content-links-login">
              <q-btn  label="Back" size="18px" flat color="white" @click="goToLogin()" />
            </div>
            <div class="text-right content-links-login">
              <q-btn label="Next" size="18px" color="white" text-color="blue-9" type="submit" />
            </div>
          </div>
        </q-form>
      </div>

    </div>
    <div class="flex register-right-section" style="height: 100vh;">
      <img src="~assets/myhhub_logo_v2.svg" alt="MyHhub" class="rounded logo-main" />
    </div>


  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        firstName: '',
        middleName: '',
        lastName: '',
        dob: '',
        ssn: '',
        phone: '',
        email: '',
        street: '',
        suite: '',
        city: '',
        state: '',
        country: '',
        zip: '',
      },
      countries: [
        { label: 'United States', value: 'US' },
        { label: 'Canada', value: 'CA' },
        { label: 'Mexico', value: 'MX' },
      ],
    };
  },
  methods: {
    handleSubmit() {
      if (this.$refs.form.validate()) {
        console.log('Form submitted:', this.form);
      } else {
        console.log('Validation failed');
      }
    },
    goToLogin(){
        this.$router.push("login");
    }
  },
};
</script>
