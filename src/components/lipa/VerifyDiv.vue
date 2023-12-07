<template>
  <div id="verify-lipa">
    <div
      id="verify-container"
      class="verify-container-entrance"
      ref="verifyContainer"
    >
      <div id="verify-1" class="verify-1-entrance" ref="verify1">
        <div class="verify-icon" id="business-permit-enrollment-icon"></div>
        <div class="verify-content">
          <h3>BUSINESS PERMIT ENROLLMENT</h3>
          <p>
            Business permit enrollment is a critical step in establishing the
            legal foundation for a business entity. This formal process involves
            submitting necessary documentation and information to local
            authorities, indicating the intent to operate a business within a
            specific jurisdiction. The enrollment typically requires details
            about the business's nature, location, ownership structure, and
            operational plans. By undergoing this procedure, businesses
            demonstrate their commitment to regulatory compliance, ensuring
            adherence to local ordinances, zoning regulations, and licensing
            requirements. Obtaining a business permit not only grants legal
            authorization for operations but also fosters transparency,
            contributing to a stable business environment and bolstering the
            overall economic integrity of the community.
          </p>
        </div>
      </div>
      <div id="verify-2" class="verify-2-entrance" ref="verify2">
        <div class="verify-icon" id="real-property-icon"></div>
        <div class="verify-content">
          <h3>REAL PROPERTY ENROLLMENT</h3>
          <p>
            Real property enrollment is a pivotal procedure in the legal
            framework of real estate ownership. This formal process involves
            registering pertinent details of a property with local authorities
            to establish legal ownership. Property enrollment typically requires
            comprehensive information, including ownership details, property
            boundaries, and relevant documentation like deeds. This crucial step
            ensures transparency in property transactions and establishes a
            clear legal foundation for ownership rights. The enrollment process
            varies by jurisdiction, but it generally contributes to the
            maintenance of accurate public records, facilitating smooth real
            estate transactions and minimizing disputes. Real property
            enrollment is essential for property owners seeking legal
            recognition and protection of their investment in a given locality.
          </p>
        </div>
      </div>
      <div id="verify-3" class="verify-3-entrance" ref="verify3">
        <div class="verify-icon" id="request-new-tax-dec-no-icon"></div>
        <div class="verify-content">
          <h3>REQUEST NEW TAX DECLARATION NO.</h3>
          <p>
            Requesting a new tax declaration number is a vital process for
            individuals and businesses initiating or undergoing significant
            changes in their financial status or property ownership. This formal
            request is made to tax authorities and involves providing detailed
            information about the entity or individual, such as personal
            identification details, financial records, or property ownership
            documents. The issuance of a new tax declaration number ensures
            accurate and up-to-date taxation records, facilitating compliance
            with tax regulations. This process is crucial in maintaining the
            integrity of the tax system, allowing for proper assessment,
            collection, and documentation of taxes based on the most current and
            relevant information available.
          </p>
        </div>
      </div>
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
      const verifyContainerElement = this.$refs.verifyContainer;
      const verify1Element = this.$refs.verify1;
      const verify2Element = this.$refs.verify2;
      const verify3Element = this.$refs.verify3;

      if (verifyContainerElement) {
        this.observer = new IntersectionObserver(
          (entries) => {
            entries.forEach((entry) => {
              if (entry.isIntersecting) {
                verifyContainerElement.classList.add(
                  "verify-container-entrance"
                );
              } else {
                verifyContainerElement.classList.remove(
                  "verify-container-entrance"
                );
              }
            });
          },
          { threshold: 0.5 }
        );

        this.observer.observe(verifyContainerElement);
      }

      if (verify1Element) {
        this.observer = new IntersectionObserver(
          (entries) => {
            entries.forEach((entry) => {
              if (entry.isIntersecting) {
                verify1Element.classList.add("verify-1-entrance");
              } else {
                verify1Element.classList.remove("verify-1-entrance");
              }
            });
          },
          { threshold: 0.5 }
        );

        this.observer.observe(verify1Element);
      }

      if (verify2Element) {
        this.observer = new IntersectionObserver(
          (entries) => {
            entries.forEach((entry) => {
              if (entry.isIntersecting) {
                verify2Element.classList.add("verify-2-entrance");
              } else {
                verify2Element.classList.remove("verify-2-entrance");
              }
            });
          },
          { threshold: 0.5 }
        );

        this.observer.observe(verify2Element);
      }

      if (verify3Element) {
        this.observer = new IntersectionObserver(
          (entries) => {
            entries.forEach((entry) => {
              if (entry.isIntersecting) {
                verify3Element.classList.add("verify-3-entrance");
              } else {
                verify3Element.classList.remove("verify-3-entrance");
              }
            });
          },
          { threshold: 0.5 }
        );

        this.observer.observe(verify3Element);
      }
    },
  },
};
</script>

<style lang="scss" scoped>
#verify-lipa {
  background-color: transparent;
  color: #2b2b2b;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  box-sizing: border-box;
  overflow-x: hidden;
  height: 100%;
  min-height: 90vh;
  display: flex;
  align-items: bottom;
  justify-content: center;
}

#verify-title {
  flex: 2;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

#verify-title h2 {
  border-bottom: 2px solid #e23a36;
  color: #e23a36;
}

#verify-container {
  flex: 5;
  display: flex;
  gap: 5px;
  align-items: center;
  justify-content: center;
  opacity: 0;
  box-sizing: border-box;
}

.verify-container-entrance {
  animation: entrance 3s ease-in-out forwards;
}

@keyframes entrance {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

#verify-1,
#verify-2,
#verify-3 {
  width: 30%;
  height: 600px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  box-sizing: border-box;
  transition: 0.3s ease-in-out;
}

.verify-icon {
  width: 200px;
  height: 200px;
  background-position: center;
  background-repeat: no-repeat;
  background-size: contain;
}

#business-permit-enrollment-icon {
  background-image: url("../../assets/business-permit-enrollment.png");
}

#real-property-icon {
  background-image: url("../../assets/real-property-enrollment.png");
}

#request-new-tax-dec-no-icon {
  background-image: url("../../assets/req-new-tax-dec-no.png");
}

.verify-content {
  flex: 3;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  box-sizing: border-box;
}

.verify-content h3 {
  height: 20%;
  color: #e23a36;
  text-align: center;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.verify-content p {
  height: 80%;
  text-align: justify;
  padding: 10px;
}

@media screen and (max-width: 1600px) {
  #verify-1,
  #verify-2,
  #verify-3 {
    height: 700px;
  }

  .verify-icon {
    width: 200px;
    height: 200px;
  }
}

@media screen and (max-width: 1300px) {
  #verify-1,
  #verify-2,
  #verify-3 {
    height: 750px;
  }
}

@media screen and (max-width: 1100px) {
  #verify-container {
    flex-direction: column;
  }

  #verify-container {
    flex-direction: column;
    animation: none;
    opacity: 1;
  }

  #verify-1,
  #verify-2,
  #verify-3 {
    width: 80%;
    height: 100%;
    opacity: 0;
  }

  .verify-1-entrance {
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

  .verify-2-entrance {
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

  .verify-3-entrance {
    animation: entrance-3 2s ease-in-out forwards;
  }

  @keyframes entrance-3 {
    from {
      opacity: 0;
    }
    to {
      opacity: 1;
    }
  }
}

@media screen and (max-width: 900px) {
  #verify-lipa {
    margin-top: 40px;
    padding: 0;
  }

  #verify-1,
  #verify-2,
  #verify-3 {
    width: 90%;
    opacity: 0;
    padding: 20px 0;
  }

  .verify-icon {
    width: 150px;
    height: 150px;
  }

  .verify-content {
    width: 100%;
  }
}
</style>
