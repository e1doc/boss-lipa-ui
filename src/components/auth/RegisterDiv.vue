<template>
  <section>
    <div class="form-holder" v-if="!registerSuccess">
      <div>
        <h1>CREATE AN ACCOUNT</h1>
      </div>
      <form @submit.prevent="register">
        <div class="form-group">
          <div>
            <base-input
              label="First Name"
              placeholder="Enter first name"
              v-model="first_name"
              name="first_name"
              refs="firstname"
              type="text"
              class="mt40"
              :validationMessages="validationMessages.first_name"
            />
          </div>
          <div>
            <base-input
              label="Middle Name"
              placeholder="Enter middle name"
              v-model="middle_name"
              name="middle_name"
              refs="middlename"
              type="text"
              class="mt40"
              :validationMessages="validationMessages.middle_name"
            />
          </div>
          <div>
            <base-input
              label="Last Name"
              placeholder="Enter last name"
              v-model="last_name"
              name="last_name"
              refs="lastname"
              type="text"
              class="mt40"
              :validationMessages="validationMessages.last_name"
            />
          </div>
          <div>
            <base-input
              label="User Name"
              placeholder="Enter user name"
              v-model="username"
              name="username"
              refs="user_name"
              type="text"
              class="mt40"
              :validationMessages="validationMessages.username"
            />
          </div>
          <!--
          <div>
            <div class="gender-radio">
              <div>
                <input
                  type="radio"
                  id="male"
                  value="M"
                  v-model="sex"
                  name="gender"
                />
                <label for="male">Male</label>
              </div>
              <div>
                <input
                  type="radio"
                  id="female"
                  value="F"
                  v-model="sex"
                  name="gender"
                />
                <label for="female">Female</label>
              </div>
            </div>
          </div>
          -->
          <!--
          <div>
            <div class="gender-radio">
              <div>
                <input
                  type="radio"
                  id="male"
                  value="M"
                  v-model="sex"
                  name="sex"
                />
                <label for="male">Male</label>
              </div>
              <div>
                <input
                  type="radio"
                  id="female"
                  value="F"
                  v-model="sex"
                  name="sex"
                />
                <label for="female">Female</label>
              </div>
            </div>
          </div>
          -->
          <div>
            <sex-input v-model="sex" />
          </div>
          <div>
            <base-input
              label="Email"
              placeholder="Enter email"
              v-model="email"
              name="email"
              refs="user_email"
              type="email"
              class="mt40"
              :validationMessages="validationMessages.email"
            />
          </div>
          <div>
            <base-input
              label="Confirm Email"
              placeholder="Confirm Email"
              v-model="confirm_email"
              name="email"
              refs="confirm_email"
              type="email"
              class="mt40"
              :validationMessages="validationMessages.confirm_email"
            />
          </div>
          <div class="meta-tel-holder">
            <base-tel-number
              v-model="phone_number"
              class="mb20"
              :validationMessages="validationMessages.phone_number"
            />
          </div>
          <div>
            <base-input
              label="Password"
              placeholder="Enter password"
              v-model="password"
              name="password"
              refs="user_password"
              type="password"
              class="mt40"
              :validationMessages="validationMessages.password"
            />
          </div>
          <div>
            <button-full class="mt10" type="submit">
              REGISTER
            </button-full>
          </div>
        </div>
      </form>
    </div>
    <div class="form-success" v-if="registerSuccess">
      <div class="mb30">
        <font-awesome-icon icon="user-circle" class="icon" />
      </div>
      <div class="mb30">
        <h1>ACCOUNT REGISTRATION</h1>
      </div>
      <div class="note mb30">
        Thank you for signing up with us. As a final step, kindly activate your
        account by logging in using your registered username and password. Your
        activation link will be sent to you upon your first login. Please click
        on the link emailed to you to activate your account
      </div>
      <div class="note">
        Thank you for signing up with us. You can now login to Lipa One Stop
        Shop (BOSS) App using your registered username and password.
      </div>
    </div>
  </section>
</template>

<script>
import ButtonFull from "@/components/ButtonFull";
import ButtonFullOutline from "@/components/ButtonFullOutline";
import BaseInput from "@/components/forms/BaseInput";
import BaseTelNumber from "@/components/forms/BaseTelNumber";
import SexInput from "@/components/lipa/SexInput";
import { mapGetters, mapActions } from "vuex";
export default {
  name: "RegisterDiv",
  components: {
    ButtonFull,
    BaseInput,
    BaseTelNumber,
    SexInput,
  },
  data() {
    return {
      first_name: "",
      middle_name: "",
      last_name: "",
      username: "",
      sex: "",
      email: "",
      confirm_email: "",
      phone_number: "",
      password: "",
      isSuccess: false,
    };
  },
  computed: {
    ...mapGetters(["registerSuccess", "validationMessages"]),
  },
  mounted() {},
  methods: {
    ...mapActions(["registerUser"]),
    async register() {
      let payload = {
        username: this.username,
        first_name: this.first_name,
        last_name: this.last_name,
        middle_name: this.middle_name,
        sex: this.sex,
        email: this.email,
        password: this.password,
        phone_number: this.phone_number,
      };

      console.log(payload);

      this.$store.commit("setValidationMessages", {
        confirm_email: [],
      });

      if (payload.email !== this.confirm_email) {
        this.$store.commit("setValidationMessages", {
          confirm_email: ["Email and confirmation email must match."],
        });

        return false;
      }

      await this.registerUser(payload);
    },
  },
};
</script>

<style lang="scss" scoped>
.meta-tel-holder {
  margin-bottom: 15px !important;
}
.form-success {
  margin-top: 60px;
  .icon {
    font-size: 80px;
    color: #c2c2c2;
  }
}
.form-group {
  margin-top: 40px;
}
.note {
  font-size: 14px;
  line-height: 26px;
  letter-spacing: 0.5px;
}

/* SEX */
.gender-radio {
  margin-bottom: 15px;
}

.gender-radio div {
  display: inline-block;
  margin-right: 10px;
}

.gender-radio div input[type="radio"] {
  margin-right: 5px;
}

@media only screen and (max-width: 860px) {
  h1 {
    font-size: 22px;
  }
  .form-group {
    margin-top: 30px;
  }
}

@media only screen and (max-width: 350px) {
  h1 {
    font-size: 20px;
  }
}
</style>
