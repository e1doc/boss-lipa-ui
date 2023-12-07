<template>
  <section>
    <div class="sc-home">
      <div id="home-content">
        <div class="home-left">
          <div class="home-left-content" id="home-business-permit-enrollment">
            <h3>BUSINESS PERMIT ENROLLMENT</h3>
            <p>
              Ease into the process of securing your business permit with our
              straightforward enrollment, designed to simplify your application
              experience.
              <br /><br />
              Simply click the "PROCEED" button below to navigate to the
              business permit enrollment.
            </p>
            <router-link
              :to="{ name: 'BusinessPermitEnrollment' }"
              class="link"
            >
              <button>PROCEED</button>
            </router-link>
          </div>
          <div class="home-left-content" id="home-real-property-enrollment">
            <h3>REAL PROPERTY ENROLLMENT</h3>
            <p>
              Simplify your real property journey by commencing the
              straightforward enrollment process tailored for your convenience
              and property documentation needs.
              <br /><br />
              Simply click the "PROCEED" button below to navigate to the request
              real property enrollment.
            </p>
            <router-link :to="{ name: 'Profile' }" class="link">
              <button @click="proceedToRealProperty">PROCEED</button>
            </router-link>
          </div>
          <div class="home-left-content" id="req-new-tax-dec">
            <h3>REQUEST NEW TAX DECLARATION NUMBER</h3>
            <p>
              Initiate the process for obtaining a new tax declaration number
              with our simple and user-friendly application for your
              convenience.
              <br /><br />
              Simply click the "PROCEED" button below to request new tax
              declaration number.
            </p>
            <router-link :to="{ name: 'RequestNewTaxDec' }" class="link">
              <button>PROCEED</button>
            </router-link>
          </div>
        </div>
        <div class="home-right">
          <div class="home-right-content" id="home-building-permit">
            <h3>BUILDING PERMIT APPLICATION</h3>
            <p>
              Start your building permit application effortlessly and pave the
              way for a smooth construction process.
              <br /><br />
              Simply click the "PROCEED" button below to navigate to the
              business permit application.
            </p>
            <!--
            <router-link
              :to="{ name: 'BuildingPermitApplication' }"
              class="link"
            >
              <button>PROCEED</button>
            </router-link>
          -->
            <button @click="showGuide('BuildingPermitApplication')">
              PROCEED
            </button>
          </div>
          <div class="home-right-content" id="home-business-permit">
            <h3>BUSINESS PERMIT APPLICATION</h3>
            <p>
              Embark on your business journey smoothly by initiating the
              straightforward business permit application process designed for
              your convenience.
              <br /><br />
              Simply click the "PROCEED" button below to navigate to the
              building permit application.
            </p>
            <!--
            <router-link
              :to="{ name: 'BusinessPermitApplication' }"
              class="link"
            >
              <button>PROCEED</button>
            </router-link>
            -->
            <button @click="showGuide('BusinessPermitApplication')">
              PROCEED
            </button>
          </div>
        </div>

        <div class="blur-background" v-if="showBlur"></div>

        <div v-if="showGuideFlag" class="guide focused-div">
          <div class="title">
            <h3>INSTRUCTIONS</h3>
          </div>

          <div class="content">
            <div class="left">
              <ul class="steps">
                <li>
                  <h4>Basic Information:</h4>
                  <p>
                    Provide your full name when requested for basic information
                    to ensure accurate identification.
                  </p>
                </li>
                <li>
                  <h4>Business/Building Details:</h4>
                  <p>
                    For business or building details, include essential
                    information such as the company name, address, and contact
                    details to facilitate accurate communication and
                    identification.
                  </p>
                </li>
                <li>
                  <h4>Upload Requirements:</h4>
                  <p>
                    Make sure to adhere to upload requirements by following
                    specified formats and sizes to ensure successful submission
                    of your files.
                  </p>
                </li>
                <li>
                  <h4>Application Submission:</h4>
                  <p>
                    Complete the application submission process by carefully
                    filling out all required fields and attaching any necessary
                    documents before finalizing and submitting your application.
                  </p>
                </li>
              </ul>
            </div>
            <div class="right">
              <div class="form">
                <h4>Business/Building Permit Application</h4>

                <label for="">Name:</label>
                <input type="text" disabled /><br />
                <label for="">Email:</label>
                <input type="text" disabled /><br />
                <label for="">Contact:</label>
                <input type="text" disabled /><br />
                <label for="">Business Details:</label>
                <textarea cols="30" rows="5" disabled></textarea><br />
                <label for="">Building Details:</label>
                <textarea cols="30" rows="5" disabled></textarea><br />
              </div>
            </div>
          </div>

          <button class="close" @click="closeGuide">
            X
          </button>
          <button class="next" @click="proceedToDestination">NEXT</button>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import ButtonFull from "@/components/ButtonFull";
import ButtonFullOutline from "@/components/ButtonFullOutline";
import BaseInputIcon from "@/components/forms/BaseInputIcon";
import ProfileTableMenu from "@/components/tables/ProfileTableMenu";
import ProfileTable from "@/components/tables/ProfileTable";
import TransactionTable from "@/components/tables/TransactionTable";
import ApplicationTable from "@/components/tables/ApplicationTable";
import InvoiceDialog from "@/components/payment/InvoiceDialog";
import HeaderNav from "@/components/HeaderNav";
import UserProfile from "@/components/UserProfile";
import DownloadableInvoice from "@/components/payment/DownloadableInvoice";
import { mapGetters } from "vuex";

export default {
  components: {
    ButtonFull,
    ButtonFullOutline,
    BaseInputIcon,
    ProfileTableMenu,
    ProfileTable,
    TransactionTable,
    ApplicationTable,
    InvoiceDialog,
    HeaderNav,
    UserProfile,
    DownloadableInvoice,
  },
  name: "Home",
  data() {
    return {
      text1: "",
      text2: "",
      showGuideFlag: false,
      showBlur: false,
      destination: "",
    };
  },
  methods: {
    proceedToRealProperty() {
      this.$router.push({ name: "Profile" });
      this.$store.commit("setCurrentTable", "profile");
      this.$store.commit("setCurrentType", "real_property");
    },
    showGuide(destination) {
      window.scrollTo({ top: 0, behavior: "smooth" });

      this.showGuideFlag = true;
      this.showBlur = true;
      this.destination = destination;
    },
    closeGuide() {
      this.showGuideFlag = false;
      this.showBlur = false;
    },
    proceedToDestination() {
      this.showGuideFlag = false;
      this.showBlur = false;
      this.$router.push({ name: this.destination });
    },
  },
};
</script>

<style lang="scss" scoped>
.sc-home {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  box-sizing: border-box;
}

#home-content {
  width: 80%;
  height: 90vh;
  margin: 0;
  padding: 40px;
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 40px;
}

.home-left,
.home-right {
  flex: 1;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 40px;
}

.home-left-content,
.home-right-content {
  background-color: whitesmoke;
  width: 100%;
  padding: 10px;
  box-sizing: border-box;
  box-shadow: 2px 8px 12px 0px rgba(70, 70, 70, 0.5);
  background-color: #e8726f;
  box-shadow: 2px 8px 12px 0px gray;
  color: whitesmoke;
  position: relative;
}

.home-left-content {
  height: 33%;
}
.home-right-content {
  height: 50%;
}

.home-left-content h3,
.home-right-content h3 {
  padding: 10px;
  text-align: center;
}

.home-left-content p,
.home-right-content p {
  padding: 10px;
  text-align: justify;
}

.home-left-content button,
.home-right-content button {
  padding: 12px 18px;
  border: none;
  position: absolute;
  right: 0;
  bottom: 5px;
  background-color: whitesmoke;
  color: #2b2b2b;
  cursor: pointer;
  font-weight: bold;
  border-radius: 50px 0 0 10px;
  padding-left: 30px;
  transition: 0.3s ease-in-out;
}

.home-left-content button:hover,
.home-right-content button:hover {
  border-right: none;
  padding-left: 60px;
}

/* GUIDE */
.guide {
  background-color: #f3f3f3;
  color: #2b2b2b;
  box-shadow: 0px 0px 40px 10px rgba(10, 10, 10, 0.5);
  width: 800px;
  height: 600px;
  position: fixed;
  top: calc(50% - 300px);
  left: calc(50% - 400px);
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  border-radius: 5px;
  animation: entrance 0.3s ease-in-out forwards;
}

@keyframes entrance {
  from {
    transform: scale(0.95);
  }
  to {
    transform: scale(1);
  }
}

.guide .title {
  height: 10%;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
}

.guide .content {
  height: 90%;
  display: flex;
  gap: 2px;
}

.guide .left {
  flex: 1;
  font: 12px;
}
.guide .right {
  flex: 1;
}

.guide .left .steps {
  box-sizing: border-box;
  margin-top: 30px;
}

.guide .left ul {
  list-style-type: circle;
  margin-left: 40px;
}

.guide .left ul li h4 {
  margin: 5px 0;
}

.guide .left ul li p {
  margin: 10px 2px;
  text-align: justify;
}

.guide .right .form {
  background-color: #e8726f;
  box-shadow: 2px 8px 12px 0px gray;
  width: 80%;
  height: 80%;
  margin: auto;
  margin-top: 20px;
  display: flex;
  flex-direction: column;
  padding: 5px 20px;
  box-sizing: border-box;
  font-size: 11px;
}

.guide .right .form h4 {
  text-align: center;
  margin: 20px;
  font-size: 13px;
}

.guide .right .form input,
.guide .right .form textarea {
  padding: 3px;
  border-radius: 3px;
  border: none;
}

.guide .close {
  background-color: transparent;
  position: absolute;
  top: 10px;
  right: 5px;
  padding: 5px 10px;
  border: none;
  font-size: 18px;
  font-weight: bold;
}

.guide .next {
  padding: 12px 18px;
  border: none;
  position: absolute;
  right: 0;
  bottom: 5px;
  background-color: #e8726f;
  color: whitesmoke;
  cursor: pointer;
  font-weight: bold;
  border-radius: 50px 0 0 10px;
  padding-left: 30px;
  transition: 0.3s ease-in-out;
}

.guide .next:hover {
  border-right: none;
  padding-left: 60px;
}

/* BLUR EFFECT */

.blur-background {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  backdrop-filter: blur(3px);
  z-index: 1;
}

.focused-div {
  z-index: 2;
}

@media screen and (max-width: 1300px) {
  #home-content {
    width: 90%;
    height: 100%;
  }

  .home-left-content {
    padding-bottom: 50px;
  }

  .home-right-content {
    height: 100%;
    padding-bottom: 100px;
  }
}

@media screen and (max-width: 1100px) {
  #home-content {
    flex-direction: column;
    width: 100%;
    height: 100%;
  }

  .home-left {
    order: 2;
  }

  .home-right {
    order: 1;
  }

  .home-left-content,
  .home-right-content {
    height: 100%;
    padding-bottom: 100px;
  }
}

@media screen and (max-width: 900px) {
  #home-content {
    padding: 40px 10px;
  }

  .guide {
    height: auto;
    width: 96%;
    flex-direction: column;
    position: absolute;
    top: 10px;
    left: calc(50% - 48%);
  }

  .guide .title {
    height: 80px;
  }

  .guide .content {
    flex-direction: column;
    height: 100%;
    margin-bottom: 100px;
  }

  .guide .content .steps {
    padding: 20px;
    margin-top: 0;
    margin-left: 5px;
  }
}
</style>
