<template>
  <section class="sc-rp-enrollment">
    <div class="container">
      <div class="flex-column">
        <div>
          <h2>Real Property Enrollment</h2>
        </div>
        <enrollment-success
          v-if="isSuccess"
          type="real_property"
          :account_no="td_no"
        />
        <div v-if="!isSuccess" class="sc-rounded-div">
          <div class="form-group">
            <div class="title">
              <h3>Account Information</h3>
            </div>
            <div>
              <base-select
                placeholder="------ Choose type of property ------"
                :options="propertytype"
                v-model="property_type"
                name="selectProperty"
                class="mb15"
              />
              <base-input-icon-end
                label="ARP Number"
                placeholder="Enter ARP Number"
                v-model="td_no"
                name="td_no"
                refs="td_number"
                type="text"
                class="mt40"
                icon="id-card"
              />
            </div>
            <div>
              <base-input-icon-end
                label="Official Receipt Number"
                placeholder="Enter official receipt number"
                v-model="official_receipt"
                name="official_receipt"
                refs="or"
                type="text"
                class="mt40"
                icon="receipt"
              />
            </div>
            <div class="datepicker">
              <base-date-picker v-model="date" />
            </div>
            <div>
              <button-block @click.native="verify()"> VERIFY </button-block>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import BaseInputIconEnd from "@/components/forms/BaseInputIconEnd";
import ButtonBlock from "@/components/ButtonBlock";
import BaseDatePicker from "@/components/forms/BaseDatePicker";
import EnrollmentSuccess from "@/components/enrollment/EnrollmentSuccess";
import BaseSelect from "@/components/forms/BaseSelect";
import axios from "axios";
import { mapGetters } from "vuex";
const oneDocToken = process.env.VUE_APP_ONE_DOC_TOKEN;
const lguLocalEndpoint = process.env.VUE_APP_LGU_LOCAL_ENDPOINT;
export default {
  name: "RealPropertyEnrollment",
  components: {
    BaseInputIconEnd,
    ButtonBlock,
    BaseDatePicker,
    EnrollmentSuccess,
    BaseSelect,
  },
  computed: {
    ...mapGetters(["authToken"]),
  },
  mounted() {
    this.$store.commit("setLoading", false);
  },
  data() {
    return {
      td_no: "",
      official_receipt: "",
      date: "",
      isSuccess: false,
      property_type: "",
      required_fields: ["property_type", "td_no", "official_receipt", "date"],
      propertytype: [
        {
          label: "Land",
          value: "Land",
        },
        {
          label: "Building",
          value: "Building",
        },
        {
          label: "Machinery",
          value: "Machinery",
        },
      ],
    };
  },
  methods: {
    async verify() {
      const dateObject = new Date(this.date);
      const dateWithoutTime = dateObject.toISOString().split("T")[0];

      const year = dateObject.getFullYear();
      const month = (dateObject.getMonth() + 1).toString().padStart(2, "0"); // Month is zero-based
      const day = dateObject
        .getDate()
        .toString()
        .padStart(2, "0");

      const formattedDate = `${year}-${month}-${day}`;

      console.log(dateObject);
      console.log(dateWithoutTime);
      console.log(formattedDate);

      let payload = {
        name: "RealPropertyTaxEnrollment",
        param: {
          property_type: this.property_type,
          tdno: this.td_no,
          ordate: formattedDate,
          ornumber: this.official_receipt,
        },
      };
      await this.propertyEnrollment(payload);
    },
    async propertyEnrollment(payload) {
      try {
        this.$store.commit("setLoading", true);
        let config = {
          headers: {
            "OneDoc-Token": oneDocToken,
            "Content-Type": "application/json",
          },
        };
        console.log("working1");
        const validateResponse = await axios.get(
          `${process.env.VUE_APP_API_URL}/api/verify-enrollment/?id=${this.td_no}&type=property`,
          { headers: { Authorization: `jwt ${this.authToken}` } }
        );
        console.log(validateResponse.data);
        console.log("working2");
        if (!validateResponse.data.is_existing) {
          console.log("working3");
          console.log(payload);
          const response = await axios.post(
            `${lguLocalEndpoint}`,
            payload,
            config
          );
          console.log("working4");
          if (response.data.Status === "Success") {
            if (response.data.Result.referenceid) {
              let building_payload = {
                is_draft: false,
                is_enrolled: true,
                reference_id: response.data.Result.referenceid,
              };
              await this.$store.dispatch(
                "addBuildingApplication",
                building_payload
              );
              await this.$store.dispatch("addBuildingBasicInformation", {
                owner_first_name: response.data.Result.owner_name,
              });
              await this.$store.dispatch("addBuildingDetails", {
                tax_dec_no: response.data.Result.td_number,
                property_type: this.property_type,
              });
              this.isSuccess = true;
              this.td_no = response.data.Result.td_number;
            } else {
              this.$swal({
                title: "Failed!",
                text: response.data.Message,
                icon: "error",
              });
            }
          } else {
            this.$swal({
              title: "Failed!",
              text: response.data.Message,
              icon: "error",
            });
          }
        } else {
          this.$swal({
            title: "Failed!",
            text: "Record already enrolled.",
            icon: "error",
          });
        }
        this.$store.commit("setLoading", false);
      } catch (err) {
        console.log(err);
        this.$swal({
          title: "Failed!",
          text: "No record found.",
          icon: "error",
        });
        this.$store.commit("setLoading", false);
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.sc-rp-enrollment {
  display: flex;
  flex-wrap: wrap;
  text-align: center;
  padding: 70px 30px 50px;
  min-height: calc(100vh - 285px);
  .sc-rounded-div {
    background: #eaf6ff !important;
    max-width: 53%;
    width: 100%;
    min-height: 500px;
    margin: 50px auto 0;
    box-shadow: 0px 10px 20px #0000000d;
    .form-group {
      text-align: center;
      padding: 80px 80px 50px;
      background-color: #e8726f;
      box-shadow: 2px 8px 12px 0px gray;
      color: whitesmoke;
      .title {
        margin-bottom: 50px;
        text-align: left;
      }
      div {
        margin-bottom: 30px;
      }
    }
  }
}
.datepicker {
  width: 100%;
}

/*
MOBILE RESPONSIVENESS 
--------------------------------------------------------------*/
@media only screen and (max-width: 1400px) {
  .sc-rp-enrollment {
    .sc-rounded-div {
      max-width: 570px;
      min-height: auto;
      margin-top: 30px;
      .form-group {
        padding: 60px 60px 30px;
        .title {
          margin-bottom: 30px;
        }
        div {
          margin-bottom: 20px;
        }
      }
    }
  }
}

@media only screen and (max-width: 768px) {
  h2 {
    font-size: 20px;
  }

  .sc-rp-enrollment .sc-rounded-div .form-group {
    padding: 50px 30px 30px;
  }

  h3 {
    font-size: 17px;
  }
}

@media only screen and (max-width: 580px) {
  h2 {
    font-size: 20px;
  }
}

@media only screen and (max-width: 480px) {
  .sc-rp-enrollment {
    padding: 70px 0 30px;
  }
}

@media only screen and (max-width: 480px) {
  .sc-rp-enrollment .sc-rounded-div .form-group {
    padding: 30px 15px 10px;
  }

  h3 {
    font-size: 15px;
  }
}
</style>
