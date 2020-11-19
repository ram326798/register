<template>
  <div class="container">
    <form @submit.prevent="handleSubmit()">
      <div class="well">
        <h4>Registration</h4>
        <div class="form-group">
          <label class="pull-left"> Username </label>
          <input
            type="text"
            class="form-control"
            placeholder="Username"
            v-model="User.username"
            :class="{ 'is-invalid': submitted && $v.User.username.$error }"
          />
          <div
            v-if="submitted && $v.User.username.$error"
            class="invalid-feedback"
          >
            <span v-if="!$v.User.username.required">Username is required</span>
            <span v-if="!$v.User.username.minLength"
              >Username must be at least 6 characters</span
            >
          </div>
        </div>
        <div class="form-group">
          <label class="pull-left"> Password </label>
          <input
            type="password"
            class="form-control"
            placeholder="Password "
            v-model="User.password"
            :class="{ 'is-invalid': submitted && $v.User.password.$error }"
          />
          <div
            v-if="submitted && $v.User.password.$error"
            class="invalid-feedback"
          >
            <span v-if="!$v.User.password.required">Password is required</span>
            <span v-if="!$v.User.password.minLength">Password must be at least 6 characters</span
            >
          </div>
        </div>
        <div class="form-group">
          <label class="pull-left"> Address </label>
          <input
            type="text"
            class="form-control"
            placeholder="Address "
            v-model="User.address"
            :class="{ 'is-invalid': submitted && $v.User.address.$error }"
          />
          <div
            v-if="submitted && !$v.User.address.required"
            class="invalid-feedback"
          >
            Address is required
          </div>
        </div>
        <div class="form-group">
          <label class="pull-left"> State </label>
          <input
            type="text"
            class="form-control"
            placeholder="State "
            v-model="User.state"
            :class="{ 'is-invalid': submitted && $v.User.state.$error }"
          />
          <div
            v-if="submitted && !$v.User.state.required"
            class="invalid-feedback"
          >
            State is required
          </div>
        </div>
        <div class="form-group">
          <label class="pull-left"> Country </label>
          <input
            type="text"
            class="form-control"
            placeholder="Country "
            v-model="User.country"
            :class="{ 'is-invalid': submitted && $v.User.country.$error }"
          />
          <div
            v-if="submitted && !$v.User.country.required"
            class="invalid-feedback"
          >
            Country is required
          </div>
        </div>
        <div class="form-group">
          <label class="pull-left"> Email Address </label>
          <input
            type="email"
            class="form-control"
            placeholder="Email "
            v-model="User.emailAddress"
            :class="{ 'is-invalid': submitted && $v.User.emailAddress.$error }"
          />
          <div
            v-if="submitted && $v.User.emailAddress.$error"
            class="invalid-feedback"
          >
            <span v-if="!$v.User.emailAddress.required"
              >Email Address is required</span
            >
            <span v-if="!$v.User.emailAddress.email">Email is Invalid</span>
          </div>
        </div>
        <div class="form-group">
          <label class="pull-left"> PAN </label>
          <input
            type="text"
            class="form-control"
            placeholder="PAN number "
            v-model="User.pan"
            :class="{ 'is-invalid': submitted && $v.User.pan.$error }"
          />
          <div v-if="submitted && $v.User.pan.$error" class="invalid-feedback">
            <span v-if="!$v.User.pan.required">Pan is required</span>
            <span v-if="!$v.User.pan.minLength"
              >Pan must be at least 6 characters</span
            >
            <span v-if="!$v.User.pan.maxLength"
              >Pan must be at least 10 characters</span
            >
          </div>
        </div>
        <div class="form-group">
          <label class="pull-left"> Contact Number </label>
          <input
            type="text"
            class="form-control"
            placeholder="Contact "
            v-model="User.contactNo"
            :class="{ 'is-invalid': submitted && $v.User.contactNo.$error }"
          />
          <div
            v-if="submitted && $v.User.contactNo.$error"
            class="invalid-feedback"
          >
            <span v-if="!$v.User.contactNo.required"
              >Contact Number is required</span
            >
            <span v-if="!$v.User.contactNo.minLength"
              >Contact Number must be at least 6 digits</span
            >
            <span v-if="!$v.User.contactNo.maxLength"
              >Contact Number must be at least 10 digits</span
            >
          </div>
        </div>
        <div class="form-group">
          <label class="pull-left"> Date of birth </label>
          <input
            type="text"
            class="form-control"
            placeholder="Date of birth "
            v-model="User.dob"
            :class="{ 'is-invalid': submitted && $v.User.dob.$error }"
          />
          <div
            v-if="submitted && !$v.User.dob.required"
            class="invalid-feedback"
          >
            Date of birth is required
          </div>
        </div>
        <div class="form-group">
          <label class="pull-left"> Account Type </label>
          <input
            type="text"
            class="form-control"
            placeholder="Account type "
            v-model="User.accountType"
            :class="{ 'is-invalid': submitted && $v.User.accountType.$error }"
          />
          <div
            v-if="submitted && !$v.User.accountType.required"
            class="invalid-feedback"
          >
            Account Type is required
          </div>
        </div>
      </div>
      <button
        type="submit"
        class="btn btn-large btn-block btn-success full-width"
      >
        Submit
      </button>
      <br />
      <router-link to="/accounts/login">
        <button class="btn btn-large btn-block btn-danger full-width">
          Cancel
        </button>
      </router-link>
    </form>
  </div>
</template>

<script>
/*eslint-disable */
import axios from "axios";
import {
  required,
  email,
  minLength,
  maxLength,
} from "vuelidate/lib/validators";
export default {
  // name: 'Register',

  data() {
    return {
      User: {
        // name: "",
        username: "",
        password: "",
        address: "",
        state: "",
        country: "",
        emailAddress: "",
        pan: "",
        contactNo: "",
        dob: "",
        accountType: "",
      },
      submitted: false,
    };
  },
  validations: {
    User: {
      name: { required, minLength: minLength(6) },
      username: { required, minLength: minLength(6) },
      password: { required },
      address: { required },
      state: { required },
      country: { required },
      emailAddress: { required, email },
      pan: { required, minLength: minLength(6), maxLength: maxLength(10) },
      contactNo: {
        required,
        minLength: minLength(10),
        maxLength: maxLength(12),
      },
      dob: { required },
      accountType: { required },
    },
  },
  methods: {
    handleSubmit() {
      this.submitted = true;
      // stop here if form is invalid
      this.$v.$touch();
      if (this.$v.$invalid) {
        return;
      }
      let newUser = {
        // name: this.User.name,
        username: this.User.username,
        password: this.User.password,
        address: this.User.address,
        state: this.User.state,
        country: this.User.country,
        emailAddress: this.User.emailAddress,
        pan: this.User.pan,
        contactNo: this.User.contactNo,
        DOB: this.User.dob,
        accountType: this.User.accountType,
      };
      console.log(newUser);
      axios
        .post("http://127.0.0.1:5000/accounts/signup", newUser)
        .then((response) => {
          console.log(response);
          router.push({ name: 'Login' });
        })
        .catch((error) => {
          console.log(error.response);
        });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
