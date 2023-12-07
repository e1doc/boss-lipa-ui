<template>
  <div id="permit-lipa">
    <div id="permit-1" ref="permit1" class="entrance-trigger">
      <div class="permit-icon" id="building-permit-icon"></div>
      <div class="permit-content">
        <h3>APPLICATION FOR BUILDING PERMIT</h3>
        <p>
          The building permit application is a pivotal initial step in the
          construction process, serving as the gateway to lawful and safe
          building practices. This formal request is submitted to local
          authorities, providing a comprehensive overview of proposed
          construction or renovation projects. Essential details such as
          architectural plans, engineering specifications, and project scopes
          are included, enabling authorities to assess compliance with safety
          codes, zoning regulations, and other municipal requirements. The
          building permit application process not only ensures the structural
          integrity of constructions but also promotes community safety and
          adherence to established standards. It acts as a vital tool in shaping
          responsible urban development, fostering sustainable practices, and
          maintaining the overall well-being of a locality.
        </p>
      </div>
    </div>
    <div id="permit-2" ref="permit2" class="permit-2-entrance">
      <div class="permit-content">
        <h3>APPLICATION FOR BUSINESS PERMIT</h3>
        <p>
          The business permit application is a fundamental component of
          establishing and legitimizing a business within a given jurisdiction.
          This formal request is submitted to local government agencies,
          outlining essential details about the nature of the business, its
          location, and operational plans. The application process serves as a
          regulatory mechanism, ensuring that businesses comply with local
          ordinances, zoning regulations, and licensing requirements. Through
          this process, authorities evaluate the legitimacy and adherence to
          safety standards, contributing to the overall economic and community
          well-being. Obtaining a business permit not only provides legal
          authorization to operate but also signals a commitment to responsible
          and compliant business practices within the established legal
          framework.
        </p>
      </div>
      <div class="permit-icon" id="business-permit-icon"></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      text: "",
      observer: null,
    };
  },
  mounted() {
    this.observeElement();
  },
  methods: {
    observeElement() {
      const permit1Element = this.$refs.permit1;
      const permit2Element = this.$refs.permit2;

      if (permit1Element) {
        this.observer = new IntersectionObserver(
          (entries) => {
            entries.forEach((entry) => {
              if (entry.isIntersecting) {
                permit1Element.classList.add("permit-1-entrance");
              } else {
                permit1Element.classList.remove("permit-1-entrance");
              }
            });
          },
          { threshold: 0.5 }
        );

        this.observer.observe(permit1Element);
      }

      if (permit2Element) {
        this.observer = new IntersectionObserver(
          (entries) => {
            entries.forEach((entry) => {
              if (entry.isIntersecting) {
                permit2Element.classList.add("permit-2-entrance");
              } else {
                permit2Element.classList.remove("permit-2-entrance");
              }
            });
          },
          { threshold: 0.5 }
        );

        this.observer.observe(permit2Element);
      }
    },
  },
};
</script>

<style lang="scss" scoped>
#permit-lipa {
  background-color: transparent;
  color: #2b2b2b;
  width: 100vw;
  height: 100%;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 10px;
  box-sizing: border-box;
  overflow-x: hidden;
}

#permit-title {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-bottom: 60px;
  color: #e23a36;
}

#permit-title h2 {
  border-bottom: 2px solid #e23a36;
  text-align: center;
}

#permit-1,
#permit-2 {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  opacity: 0;
  padding: 20px 0;
}

.permit-1-entrance {
  animation: entrance-1 2s ease-in-out forwards;
}

@keyframes entrance-1 {
  from {
    transform: translateX(20%);
    opacity: 0;
  }
  to {
    transform: translateX(0);
    opacity: 1;
  }
}

.permit-2-entrance {
  animation: entrance-2 2s ease-in-out forwards;
}

@keyframes entrance-2 {
  from {
    transform: translateX(-20%);
    opacity: 0;
  }
  to {
    transform: translateX(0);
    opacity: 1;
  }
}

.permit-icon {
  width: 250px;
  height: 200px;
  background-position: center;
  background-repeat: no-repeat;
  background-size: contain;
}

#building-permit-icon {
  background-image: url("../../assets/building-permit.png");
}

#business-permit-icon {
  background-image: url("../../assets/business-permit.png");
}

.permit-content {
  width: 50%;
  height: 80%;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.permit-content h3 {
  text-align: center;
  padding-top: 10px;
  color: #e23a36;
}

.permit-content p {
  text-align: justify;
  padding: 40px;
}

#permit-2 .permit-icon {
  order: 2;
}

#permit-2 .permit-content {
  order: 1;
}

@media screen and (max-width: 1100px) {
  #permit-lipa {
    padding-top: 150px;
    padding-bottom: 20px;
  }
}

@media screen and (max-width: 900px) {
  #permit-lipa {
    padding: 150px 10px 20px 10px;
  }

  #permit-title {
    margin-bottom: 20px;
  }

  #permit-1,
  #permit-2 {
    display: flex;
    flex-direction: column;
  }

  .permit-content {
    width: 100%;
  }

  .permit-icon {
    width: 150px;
    height: 150px;
  }

  .permit-content h3 {
    padding: 0 20px;
  }

  .permit-content p {
    text-align: justify;
    padding: 20px;
  }

  #permit-2 .permit-content {
    order: 2;
  }

  #permit-2 .permit-icon {
    order: 1;
  }

  .permit-1-entrance {
    animation: entrance-1 2s ease-in-out forwards;
  }

  @keyframes entrance-1 {
    from {
      opacity: 0;
    }
    to {
      opacity: 1;
    }
  }

  .permit-2-entrance {
    animation: entrance-2 2s ease-in-out forwards;
  }

  @keyframes entrance-2 {
    from {
      opacity: 0;
    }
    to {
      opacity: 1;
    }
  }
}
</style>
