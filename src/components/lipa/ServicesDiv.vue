<template>
  <div id="services-lipa">
    <div class="services-top">
      <div class="services">
        <div class="icon-container">
          <div class="icon" id="building-permit-icon"></div>
          <div class="text">
            <router-link
              :to="{ name: 'BuildingPermitApplication' }"
              class="link"
            >
              <h3>
                Building Permit Application
              </h3>
            </router-link>
            <p>
              Seamless construction starts here - Apply for your building permit
              today.
            </p>
            <button
              class="learn-more-btn"
              @click="scrollToSection('permit-lipa')"
            >
              LEARN MORE
            </button>
          </div>
        </div>
        <div class="icon-container">
          <div class="icon" id="business-permit-icon"></div>
          <div class="text">
            <router-link
              :to="{ name: 'BusinessPermitApplication' }"
              class="link"
            >
              <h3>
                Business Permit Application
              </h3>
            </router-link>
            <p>
              Ease into success with our simple and swift business permit
              application.
            </p>
            <button
              class="learn-more-btn"
              @click="scrollToSection('permit-lipa')"
            >
              LEARN MORE
            </button>
          </div>
        </div>
      </div>
    </div>
    <div class="services-bot">
      <div class="services">
        <div class="icon-container">
          <div class="icon" id="business-permit-enrollment-icon"></div>
          <div class="text">
            <router-link
              :to="{ name: 'BusinessPermitEnrollment' }"
              class="link"
            >
              <h3>
                Business Permit Enrollment
              </h3>
            </router-link>
            <p>
              Streamline your business start with our easy and efficient permit
              enrollment.
            </p>
            <button class="learn-more-btn" @click="scrollToSection('verity-1')">
              LEARN MORE
            </button>
          </div>
        </div>
        <div class="icon-container">
          <div class="icon" id="real-property-icon"></div>
          <div class="text">
            <router-link :to="{ name: 'RealPropertyEnrollment' }" class="link">
              <h3>
                Real Property Enrollment
              </h3>
            </router-link>
            <p>
              Effortless real property enrollment for seamless ownership and
              management processes.
            </p>
            <button class="learn-more-btn" @click="scrollToSection('verify-2')">
              LEARN MORE
            </button>
          </div>
        </div>
        <div class="icon-container">
          <div class="icon" id="request-new-tax-dec-no-icon"></div>
          <div class="text">
            <router-link :to="{ name: 'RequestNewTaxDec' }" class="link">
              <h3>
                Req New Tax Declaration No.
              </h3>
            </router-link>
            <p>
              Simplify the process, request your new tax declaration number
              effortlessly.
            </p>
            <button class="learn-more-btn" @click="scrollToSection('verify-3')">
              LEARN MORE
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      text: "",
    };
  },
  methods: {
    scrollToSection(targetId) {
      const targetSection = document.getElementById(targetId);

      if (targetSection) {
        targetSection.scrollIntoView({ behavior: "smooth" });
      }
    },
  },
};
</script>

<style lang="scss" scoped>
#services-lipa {
  background-color: transparent;
  width: 80%;
  height: 100%;
  min-height: 90vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  box-sizing: border-box;
  margin-bottom: 80px;
  overflow-x: hidden;
}

.services-top,
.services-bot {
  width: 100%;
  height: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.services {
  display: flex;
  width: 80%;
  height: 80%;
  align-items: center;
  justify-content: center;
}

.icon-container {
  flex: 1;
  height: 400px;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 20px;
}

.icon-container .learn-more-btn {
  padding: 15px 20px;
  margin-top: 10px;
  font-weight: bold;
  border: none;
  transition: 0.3s ease-in-out;
}

.icon-container .learn-more-btn:hover {
  transform: scale(1.05);
}

.icon-container .text {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  background-color: transparent;
  color: #2b2b2b;
}

.icon-container .text h3 {
  color: #e23a36;
  border-bottom: 1px solid #e23a36;
}

.icon-container .text .link {
  text-decoration: none;
  color: #2b2b2b;
  border-bottom: 1px solid whitesmoke;
  margin-bottom: 10px;
  transition: transform 0.3s ease-in-out;
}

.icon-container .text .link:hover {
  transform: scale(1.03);
}

.icon-container .icon {
  background-color: transparent;
  width: 300px;
  height: 200px;
  margin-bottom: 10px;
  background-position: center;
  background-repeat: no-repeat;
  background-size: contain;
}

.icon-container #building-permit-icon {
  background-image: url("../../assets/building-permit.png");
}

.icon-container #business-permit-icon {
  background-image: url("../../assets/business-permit.png");
}

.icon-container #business-permit-enrollment-icon {
  background-image: url("../../assets/business-permit-enrollment.png");
}

.icon-container #real-property-icon {
  background-image: url("../../assets/real-property-enrollment.png");
}

.icon-container #request-new-tax-dec-no-icon {
  background-image: url("../../assets/req-new-tax-dec-no.png");
}

@media screen and (max-width: 1600px) {
  #services-lipa {
    width: 90%;
  }

  .icon-container .icon {
    width: 250px;
    height: 200px;
  }
}

@media screen and (max-width: 1300px) {
  #services-lipa {
    width: 90%;
  }

  .icon-container .icon {
    width: 250px;
    height: 200px;
  }
}

@media screen and (max-width: 1100px) {
  #services-lipa {
    width: 90%;
  }
  .icon-container .icon {
    width: 250px;
    height: 200px;
  }
}

@media screen and (max-width: 900px) {
  #services-lipa {
    width: 95%;
  }
  .services {
    flex-direction: column;
  }

  .services-top {
    height: 40%;
  }

  .services-bot {
    height: 60%;
  }

  .icon-container {
    width: 100%;
  }

  .icon-container .icon {
    width: 200px;
    height: 150px;
  }
}
</style>
