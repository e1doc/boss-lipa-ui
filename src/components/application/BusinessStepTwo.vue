<template>
  <div class="meta-container">
    <h1 class="meta-form-title">Business Details</h1>
    <div class="meta-form-group mb60">
      <div class="meta-group-title">President / Treasurer of Corporation</div>
      <base-input
        label="First Name"
        v-model="business_details.president_first_name"
        :validationMessages="
          stepTwoErrors.business_details.president_first_name
        "
        name="presidentfirstname"
        refs="pres_first_name"
        type="text"
        class="mt40"
      />
      <base-input
        label="Middle Name(optional)"
        v-model="business_details.president_middle_name"
        :validationMessages="
          stepTwoErrors.business_details.president_middle_name
        "
        name="presidentmiddlename"
        refs="pres_middle_name"
        type="text"
        class="mt40"
      />
      <base-input
        label="Last Name"
        v-model="business_details.president_last_name"
        :validationMessages="stepTwoErrors.business_details.president_last_name"
        name="presidentlastname"
        refs="pres_last_name"
        type="text"
        class="mt40"
      />
    </div>
    <div class="meta-form-group mb60">
      <div class="meta-group-title">Corporate Name:</div>
      <base-input
        label="Corporate Name"
        v-model="business_details.name"
        :validationMessages="stepTwoErrors.business_details.name"
        name="businessname"
        refs="business_name"
        type="text"
        class="mt40"
      />

      <base-input
        label="Trade Name / Franchise"
        v-model="business_details.trade_name"
        :validationMessages="stepTwoErrors.business_details.trade_name"
        name="tradename"
        refs="trade_name"
        type="text"
        class="mt40"
      />
    </div>
    <div class="meta-form-group mb60">
      <div class="meta-group-title">Business Address:</div>
      <!-- <base-input
        label="Complete Business Address"
        v-model="business_details.complete_business_address"
        :validationMessages="
          stepTwoErrors.business_details.complete_business_address
        "
        name="businessaddress"
        refs="business_address"
        type="text"
        class="mt40"
      /> -->

      <div class="meta-input-group flex-row w3">
        <base-input
          label="Address No."
          v-model="business_details.address_no"
          :validationMessages="stepTwoErrors.business_details.address_no"
          name="addressnumber"
          refs="address_no"
          type="text"
          class="input-w3"
        />
        <base-input
          label="Block"
          v-model="business_details.block_no"
          :validationMessages="stepTwoErrors.business_details.block_no"
          name="blocknumber"
          refs="block_no"
          type="text"
          class="input-w3"
        />
        <base-input
          label="Lot"
          v-model="business_details.lot_no"
          :validationMessages="stepTwoErrors.business_details.lot_no"
          name="lotnumber"
          refs="lot_no"
          type="text"
          class="input-w3"
        />
      </div>

      <div class="meta-input-group flex-row w2">
        <base-input
          label="Street"
          v-model="business_details.street"
          :validationMessages="stepTwoErrors.business_details.street"
          name="businessstreet"
          refs="business_street"
          type="text"
          class="input-w2"
        />
        <base-input
          label="Subdivision"
          v-model="business_details.subdivision"
          :validationMessages="stepTwoErrors.business_details.subdivision"
          name="subdivisionname"
          refs="subdivision"
          type="text"
          class="input-w2"
        />
      </div>

      <div class="meta-input-group flex-row w2">
        <base-input
          label="Building No."
          v-model="business_details.building_no"
          :validationMessages="stepTwoErrors.business_details.building_no"
          name="buildingnumber"
          refs="building_no"
          type="text"
          class="input-w2"
        />
        <base-input
          label="Building Name"
          v-model="business_details.building_name"
          :validationMessages="stepTwoErrors.business_details.building_name"
          name="buildingname"
          refs="building_name"
          type="text"
          class="input-w2"
        />
      </div>

      <div class="meta-input-group flex-row w2">
        <base-input
          label="Unit No."
          v-model="business_details.unit_no"
          :validationMessages="stepTwoErrors.business_details.unit_no"
          name="unitnumber"
          refs="unit_no"
          type="text"
          class="input-w2"
        />
        <base-input
          label="Floor No."
          v-model="business_details.floor_no"
          :validationMessages="stepTwoErrors.business_details.floor_no"
          name="floornumber"
          refs="floor_no"
          type="text"
          class="input-w2"
        />
      </div>

      <!-- OTHER BUSINESS DETAILS - Barangay -->
      <div class="meta-form-group mb20">
        <div class="meta-group-title no-mt">
          Barangay <span class="asterisk">*</span>
        </div>
        <base-select
          placeholder="------ Choose from the list of barangay ------"
          v-model="business_details.barangay"
          :validationMessages="stepTwoErrors.business_details.barangay"
          name="nameofbarangay"
          refs="barangay_name"
          :options="barangayname"
          type="text"
          inputClass="fw-mobile"
        />
      </div>
      <!-- OTHER BUSINESS DETAILS - City/Province -->
      <base-input
        label="City / Province"
        v-model="business_details.city"
        :validationMessages="stepTwoErrors.business_details.city"
        name="cityprovince"
        refs="city_province"
        type="text"
        class="disabled"
        inputClass="fw-mobile disabled-input"
        :disabled="true"
      />
    </div>
    <div class="meta-form-group mb60">
      <div class="meta-group-title">Other Business Details:</div>
      <!-- OTHER BUSINESS DETAILS - Telephone/Phone Number -->
      <div class="meta-input-group">
        <base-input
          label="Telephone/Phone No."
          v-model="business_details.telephone_number"
          :validationMessages="stepTwoErrors.business_details.telephone_number"
          name="businesstelephone"
          refs="business_telephone"
          type="tel"
          class="mt40 input-required"
        />
        <!-- <base-input
            label="Mobile No."
            v-model="businessmobile"
            name="businessmobile"
            refs="business_mobile"
            type="number"
            class="mt40 input-w2"
        /> -->
        <!-- <base-tel-number
          v-model="business_details.mobile_number"
          :validationMessages="stepTwoErrors.business_details.mobile_number"
          class="mb15 input-phone input-w2"
          placeholder="Mobile No."
        /> -->
      </div>

      <base-input
        label="Email Address"
        v-model="business_details.email_address"
        :validationMessages="stepTwoErrors.business_details.email_address"
        name="businessemail"
        refs="business_email"
        type="email"
        class="mt40"
      />

      <base-input
        label="Property Index Pin (PIN)"
        v-model="business_details.property_index_number"
        :validationMessages="
          stepTwoErrors.business_details.property_index_number
        "
        name="pin"
        refs="pin_number"
        type="text"
        class="mt40"
      />

      <base-input
        label="Business Area"
        v-model="business_details.area"
        :validationMessages="stepTwoErrors.business_details.area"
        name="area"
        refs="business_area"
        type="number"
        class="mt40 input-required"
      />

      <base-input
        label="Total No. of Employees(including owner)"
        v-model="business_details.total_employees"
        :validationMessages="stepTwoErrors.business_details.total_employees"
        name="total_employees"
        refs="employees"
        type="text"
        class="mt40 input-required"
      />

      <base-input
        label="No. of Employees residing in City/Municipality"
        v-model="business_details.residing_employees"
        :validationMessages="stepTwoErrors.business_details.residing_employees"
        name="residing_employees"
        refs="ref_residing_employees"
        type="number"
        class="mt40"
      />
    </div>
    <div class="meta-form-group mb60">
      <div class="meta-group-title">
        If Place of business is rented, please identify the following Lessor's
        Details:
      </div>
      <base-input
        label="First Name"
        v-model="lessor_details.first_name"
        :validationMessages="stepTwoErrors.lessor_details.first_name"
        name="lessorfirstname"
        refs="lessor_firstname"
        type="text"
        class="mt40"
      />
      <base-input
        label="Middle Name(optional)"
        v-model="lessor_details.middle_name"
        :validationMessages="stepTwoErrors.lessor_details.middle_name"
        name="lessormiddlename"
        refs="lessor_middlename"
        type="text"
        class="mt40"
      />
      <base-input
        label="Last Name"
        v-model="lessor_details.last_name"
        :validationMessages="stepTwoErrors.lessor_details.last_name"
        name="lessorlastname"
        refs="lessor_lastname"
        type="text"
        class="mt40"
      />
      <base-input
        label="Complete Address"
        v-model="lessor_details.complete_address"
        :validationMessages="stepTwoErrors.lessor_details.complete_address"
        name="lessoraddress"
        refs="lessor_address"
        type="text"
        class="mt40"
      />

      <div class="meta-input-label">Gross Monthly Rental :</div>
      <currency-input
        label="Gross Monthly Rental"
        v-model="lessor_details.gross_monthly_rental"
        :validationMessages="stepTwoErrors.lessor_details.gross_monthly_rental"
        name="monthlyrental"
        refs="monthly_rental"
        type="text"
        :isAmount="true"
        class="mt40 gross-monthly-rental-input"
        placeholder="Enter Gross Monthly Rental"
      />

      <div class="meta-input-group">
        <base-input
          label="Telephone / Phone No."
          v-model="lessor_details.telephone_number"
          :validationMessages="stepTwoErrors.lessor_details.telephone_number"
          name="lessortelephone"
          refs="lessor_telephone"
          type="tel"
          class="mt40"
        />
        <!-- <base-tel-number
          v-model="lessor_details.mobile_number"
          :validationMessages="stepTwoErrors.lessor_details.mobile_number"
          class="mb15 input-phone input-w2"
          placeholder="Mobile no."
        /> -->
      </div>
      <base-input
        label="Email Address"
        v-model="lessor_details.email_address"
        :validationMessages="stepTwoErrors.lessor_details.email_address"
        name="lessoremail"
        refs="lessor_email"
        type="email"
        class="mt40"
      />
    </div>

    <div class="meta-form-group p-relative mb60">
      <div class="meta-group-title">Business Activity</div>
      <div class="add-icon" @click="addActivity">
        <font-awesome-icon icon="plus-circle" />
      </div>
      <div
        class="meta-multi-group"
        v-for="(activity, index) in activities"
        :key="index"
      >
        <div class="meta-input-group flex-row w3">
          <!-- <base-input
            label="Code"
            v-model="activity.code"
            :name="`businesscode${index}`"
            :refs="`business_code${index}`"
            type="text"
            class="mt40 input-w3"
            inputClass="fw-mobile"
          /> -->
          <base-input
            label="Line of Business"
            v-model="activity.line_of_business"
            :name="`lineofbusiness${index}`"
            :refs="`line_of_business${index}`"
            type="text"
            class="mt40 input-w2"
            inputClass="fw-mobile"
            :validationMessages="
              activityErrors[index]
                ? activityErrors[index].value.line_of_business
                : []
            "
          />
          <base-input
            label="No. of Units"
            v-model="activity.units"
            :name="`businessunits${index}`"
            :refs="`business_units${index}`"
            type="number"
            class="mt40 input-w2"
            inputClass="fw-mobile"
          />
        </div>
        <div class="meta-input-label">Capitalization (for New Business) :</div>
        <currency-input
          label="Capitalization (for New Business)"
          v-model="activity.capitalization"
          :name="`capitalization${index}`"
          :refs="`business_capitalization${index}`"
          type="text"
          :isAmount="true"
          class="mt40 mb10 capitalization-input"
        />
        <div v-if="activityErrors[index]">
          <div v-if="activityErrors[index].value.capitalization">
            <div class="meta-error-text">* This field may not be blank</div>
          </div>
        </div>
        <!-- <div class="meta-group-title">
          Gross Sales / Receipts (For Renewal)
        </div> -->
        <!-- <div class="meta-input-group flex-row w2">
          <base-input
            label="Essential"
            v-model="activity.essential"
            :name="`essential${index}`"
            :refs="`renew_essential${index}`"
            type="text"
            class="mt40 input-w2"
          />
          <base-input
            label="Non-essential"
            v-model="activity.non_essential"
            :name="`nonessential${index}`"
            :refs="`non_essential${index}`"
            type="text"
            class="mt40 input-w2"
          />
        </div> -->
        <!-- <base-input
          label="Essential/Non-essential"
          v-model="activity.essential"
          :name="`essential${index}`"
          :refs="`renew_essential${index}`"
          type="text"
          class="mt40"
        /> -->
      </div>
    </div>
    <div class="meta-form-group button-left-right">
      <button-block
        type="back"
        class="back-button"
        @click.native="previousStep()"
        >BACK</button-block
      >
      <button-block class="next-button" @click.native="nextStep()"
        >NEXT</button-block
      >
    </div>
  </div>
</template>

<script>
import BaseInput from "@/components/forms/BaseInput";
import BaseSelect from "@/components/forms/BaseSelect";
import BaseCheckbox from "@/components/forms/BaseCheckbox";
import ButtonBlock from "@/components/ButtonBlock";
import BaseTelNumber from "@/components/forms/BaseTelNumber";
import { mapGetters } from "vuex";
const oneDocToken = process.env.VUE_APP_ONE_DOC_TOKEN;
const lguLocalEndpoint = process.env.VUE_APP_LGU_LOCAL_ENDPOINT;
import axios from "axios";
export default {
  name: "BusinessStepTwo",
  components: {
    BaseInput,
    BaseCheckbox,
    ButtonBlock,
    BaseSelect,
    BaseTelNumber,
  },
  data() {
    return {
      business_details: {
        name: "",
        barangay: "",
        city: "Lipa City, Batangas",
        trade_name: "",
        complete_business_address: "",
        president_first_name: "",
        president_middle_name: "",
        president_last_name: "",
        telephone_number: "",
        email_address: "",
        property_index_number: "",
        area: "",
        total_employees: "",
        residing_employees: 0,
        street: "",
        address_no: "",
        block_no: "",
        lot_no: "",
        subdivision: "",
        building_no: "",
        building_name: "",
        unit_no: "",
        floor_no: "",
      },
      lessor_details: {
        first_name: "",
        middle_name: "",
        last_name: "",
        complete_address: "",
        telephone_number: "",
        mobile_number: "",
        email_address: "",
        gross_monthly_rental: "0",
      },
      activities: [],
      activity: {
        code: "",
        line_of_business: "",
        units: 1,
        capitalization: "",
        essential: "",
        non_essential: "",
      },
      unrequired: {
        business_details: [
          "president_middle_name",
          "president_first_name",
          "president_last_name",
          "email_address",
          "property_index_number",
          "residing_employees",
          "complete_business_address",
          "house_no",
          "address_no",
          "block_no",
          "lot_no",
          "subdivision",
          "building_no",
          "building_name",
          "unit_no",
          "floor_no",
        ],
        business_activities: [
          "units",
          "code",
          "essential",
          "non_essential",
          "application_year",
        ],
      },
      barangayname: [
        { label: "Adya", value: "Adya", district: "District 1" },
        { label: "Anilao", value: "Anilao", district: "District 1" },
        {
          label: "Anilao-Labac",
          value: "Anilao-Labac",
          district: "District 1",
        },
        {
          label: "Antipolo Del Norte",
          value: "Antipolo Del Norte",
          district: "District 1",
        },
        {
          label: "Antipolo Del Sur",
          value: "Antipolo Del Sur",
          district: "District 1",
        },
        { label: "Bagong Pook", value: "Bagong Pook", district: "District 1" },
        { label: "Balintawak", value: "Balintawak", district: "District 1" },
        { label: "Banaybanay", value: "Banaybanay", district: "District 1" },
        { label: "Barangay 12", value: "Barangay 12", district: "District 1" },
        { label: "Bolbok", value: "Bolbok", district: "District 1" },
        {
          label: "Bugtong na Pulo",
          value: "Bugtong na Pulo",
          district: "District 1",
        },
        { label: "Bulacnin", value: "Bulacnin", district: "District 1" },
        { label: "Bulaklakan", value: "Bulaklakan", district: "District 1" },
        { label: "Calamias", value: "Calamias", district: "District 1" },
        { label: "Cumba", value: "Cumba", district: "District 1" },
        { label: "Dagatan", value: "Dagatan", district: "District 1" },
        { label: "Duhatan", value: "Duhatan", district: "District 1" },
        { label: "Halang", value: "Halang", district: "District 1" },
        { label: "Inosloban", value: "Inosloban", district: "District 1" },
        { label: "Kayumanggi", value: "Kayumanggi", district: "District 1" },
        { label: "Latag", value: "Latag", district: "District 1" },
        { label: "Lipa", value: "Lipa", district: "District 1" },
        { label: "Lodlod", value: "Lodlod", district: "District 1" },
        { label: "Lumbang", value: "Lumbang", district: "District 1" },
        { label: "Mabini", value: "Mabini", district: "District 1" },
        { label: "Malagonlong", value: "Malagonlong", district: "District 1" },
        { label: "Malitlit", value: "Malitlit", district: "District 1" },
        { label: "Marauoy", value: "Marauoy", district: "District 1" },
        {
          label: "Mataas Na Lupa",
          value: "Mataas Na Lupa",
          district: "District 1",
        },
        {
          label: "Munting Pulo",
          value: "Munting Pulo",
          district: "District 1",
        },
        {
          label: "Pagolingin Bata",
          value: "Pagolingin Bata",
          district: "District 1",
        },
        {
          label: "Pagolingin East",
          value: "Pagolingin East",
          district: "District 1",
        },
        {
          label: "Pagolingin West",
          value: "Pagolingin West",
          district: "District 1",
        },
        { label: "Pangao", value: "Pangao", district: "District 1" },
        {
          label: "Pinagkawitan",
          value: "Pinagkawitan",
          district: "District 1",
        },
        {
          label: "Pinagtongulan",
          value: "Pinagtongulan",
          district: "District 1",
        },
        { label: "Plaridel", value: "Plaridel", district: "District 1" },
        {
          label: "Poblacion Barangay 1",
          value: "Poblacion Barangay 1",
          district: "District 1",
        },
        {
          label: "Poblacion Barangay 2",
          value: "Poblacion Barangay 2",
          district: "District 1",
        },
        {
          label: "Poblacion Barangay 3",
          value: "Poblacion Barangay 3",
          district: "District 1",
        },
        {
          label: "Poblacion Barangay 4",
          value: "Poblacion Barangay 4",
          district: "District 1",
        },
        {
          label: "Poblacion Barangay 5",
          value: "Poblacion Barangay 5",
          district: "District 1",
        },
        {
          label: "Poblacion Barangay 6",
          value: "Poblacion Barangay 6",
          district: "District 1",
        },
        {
          label: "Poblacion Barangay 7",
          value: "Poblacion Barangay 7",
          district: "District 1",
        },
        {
          label: "Poblacion Barangay 8",
          value: "Poblacion Barangay 8",
          district: "District 1",
        },
        {
          label: "Poblacion Barangay 9",
          value: "Poblacion Barangay 9",
          district: "District 1",
        },
        {
          label: "Poblacion Barangay 10",
          value: "Poblacion Barangay 10",
          district: "District 1",
        },
        {
          label: "Poblacion Barangay 11",
          value: "Poblacion Barangay 11",
          district: "District 1",
        },
        {
          label: "Poblacion Barangay 9-A",
          value: "Poblacion Barangay 9-A",
          district: "District 1",
        },
        { label: "Pusil", value: "Pusil", district: "District 1" },
        { label: "Quezon", value: "Quezon", district: "District 1" },
        { label: "Rizal", value: "Rizal", district: "District 1" },
        { label: "Sabang", value: "Sabang", district: "District 1" },
        { label: "Sampaguita", value: "Sampaguita", district: "District 1" },
        { label: "San Benito", value: "San Benito", district: "District 1" },
        { label: "San Carlos", value: "San Carlos", district: "District 1" },
        {
          label: "San Celestino",
          value: "San Celestino",
          district: "District 1",
        },
        {
          label: "San Francisco",
          value: "San Francisco",
          district: "District 1",
        },
        {
          label: "San Guillermo",
          value: "San Guillermo",
          district: "District 1",
        },
        { label: "San Jose", value: "San Jose", district: "District 1" },
        { label: "San Lucas", value: "San Lucas", district: "District 1" },
        {
          label: "San Salvador",
          value: "San Salvador",
          district: "District 1",
        },
        {
          label: "San Sebastian",
          value: "San Sebastian",
          district: "District 1",
        },
        { label: "Santo Niño", value: "Santo Niño", district: "District 1" },
        {
          label: "Santo Toribio",
          value: "Santo Toribio",
          district: "District 1",
        },
        { label: "Sapac", value: "Sapac", district: "District 1" },
        { label: "Sico", value: "Sico", district: "District 1" },
        { label: "Talisay", value: "Talisay", district: "District 1" },
        { label: "Tambo", value: "Tambo", district: "District 1" },
        { label: "Tangob", value: "Tangob", district: "District 1" },
        { label: "Tanguay", value: "Tanguay", district: "District 1" },
        { label: "Tibig", value: "Tibig", district: "District 1" },
        { label: "Tipacan", value: "Tipacan", district: "District 1" },
      ],
    };
  },
  computed: {
    ...mapGetters([
      "businessApplication",
      "businessDetails",
      "lessorDetails",
      "businessActivities",
      "detailsHasError",
      "lessorDetailsHasError",
      "stepTwoErrors",
      "applicationRequirements",
      "draftBusiness",
      "typeOfOrganization",
      "activityErrors",
      "businessBasicInformation",
    ]),
  },
  mounted() {
    this.scrollToTop();
    this.addActivity();
    this.preFillForm();
    this.changeTypeOfOrganization();
  },
  watch: {
    draftBusiness: {
      deep: true,
      handler(status) {
        if (status) {
          this.nextStep();
        }
      },
    },
  },
  methods: {
    scrollToTop() {
      window.scrollTo(0, 0);
    },
    changeTypeOfOrganization() {
      if (this.typeOfOrganization === "corporation") {
        if (!this.unrequired.business_details.includes("trade_name")) {
          this.unrequired.business_details.push("trade_name");
        }
        this.unrequired.business_details = this.unrequired.business_details.filter(
          (item) => item !== "name"
        );
      } else {
        if (!this.unrequired.business_details.includes("name")) {
          this.unrequired.business_details.push("name");
        }
        this.unrequired.business_details = this.unrequired.business_details.filter(
          (item) => item !== "trade_name"
        );
      }
    },
    previousStep() {
      this.$store.commit("setCurrentApplicationStep", "1");
    },
    async nextStep() {
      this.$store.commit("setLoading", true);
      if (
        this.business_details.residing_employees === 0 ||
        this.business_details.residing_employees === ""
      ) {
        this.business_details.residing_employees = 0;
      }
      if (this.businessDetails.id) {
        await this.$store.dispatch(
          "updateBusinessDetails",
          this.business_details
        );
      } else {
        await this.$store.dispatch("addBusinessDetails", this.business_details);
      }
      if (
        this.lessor_details.gross_monthly_rental === 0 ||
        this.lessor_details.gross_monthly_rental === ""
      ) {
        this.lessor_details.gross_monthly_rental = 0;
      }
      if (this.lessorDetails.id) {
        await this.$store.dispatch("updateLessorDetails", this.lessor_details);
      } else {
        await this.$store.dispatch("addLessorDetails", this.lessor_details);
      }
      if (this.businessActivities.length > 0) {
        if (this.activities.length > this.businessActivities.length) {
          let update = this.activities.slice(0, this.businessActivities.length);
          let add = this.activities.slice(this.businessActivities.length);
          await this.$store.dispatch("updateBusinessActivity", update);
          await this.$store.dispatch("addBusinessActivity", add);
        } else {
          await this.$store.dispatch("updateBusinessActivity", this.activities);
        }
        // await this.$store.dispatch("updateBusinessActivity", this.activities);
      } else {
        await this.$store.dispatch("addBusinessActivity", this.activities);
      }
      if (!this.detailsHasError && !this.lessorDetailsHasError) {
        let payload = { application_id: this.businessApplication.id };
        if (this.applicationRequirements) {
          if (!this.applicationRequirements.id) {
            this.$store.dispatch("addApplicationRequirements", payload);
          }
        }
        if (!this.draftBusiness) {
          await this.validateRequiredFields();
          this.$store.commit("setLoading", false);
        } else {
          this.$swal({
            title: "Success!",
            text: "data successfully saved as draft.",
            icon: "success",
          }).then((value) => {
            this.toProfile();
          });
        }
      } else {
        await this.validateRequiredFields();
        if (this.draftBusiness) {
          this.$swal({
            title: "Failed!",
            text: "Please fix the validation errors before saving as draft.",
            icon: "error",
          });
          this.$store.commit("setDraftBusiness", false);
        } else {
          this.$swal({
            title: "Failed!",
            text:
              "Please fix the validation errors before proceeding to the next step.",
            icon: "error",
          });
        }
      }
      this.$store.commit("setLoading", false);
    },
    toProfile() {
      this.$router.push({ name: "Profile" });
      this.$store.commit("setDraftBusiness", false);
    },
    preFillForm() {
      if (this.businessDetails.id) {
        this.business_details = this.businessDetails;
      }
      if (this.lessorDetails.id) {
        this.lessor_details = this.lessorDetails;
      }
      if (this.businessActivities.length > 0) {
        this.activities.splice(0, this.activities.length);
        this.businessActivities.forEach((element) => {
          this.activities.push(element);
        });
      }
    },
    addActivity() {
      if (this.activities) {
        if (this.activities.length < 4) {
          let activity = {
            code: "",
            line_of_business: "",
            units: "",
            capitalization: "",
            essential: "",
            non_essential: "",
          };
          this.activities.push(activity);
        }
      }
    },
    async validateRequiredFields() {
      let business_details_errors = { key: "business_details", value: {} };
      let activity_errors_holder = {};
      let isBusinessDetailsClean = true;
      let isBusinessActivitiesClean = true;
      for (let key in this.business_details) {
        if (!this.unrequired.business_details.includes(key)) {
          if (this.business_details[key] === "") {
            business_details_errors.value[`${key}`] = [];
            business_details_errors.value[`${key}`].push(
              "This field may not be blank."
            );
          }
        }
      }

      if (this.activities.length > 0) {
        let index = 0;
        for (let activity of this.activities) {
          let business_activity_errors = {
            key: "business_activities",
            value: {},
          };
          for (let key in activity) {
            if (!this.unrequired.business_activities.includes(key)) {
              if (
                activity[key] === "" ||
                activity[key] === null ||
                activity[key] === 0
              ) {
                business_activity_errors.value[`${key}`] = [];
                business_activity_errors.value[`${key}`].push(
                  "This field may not be blank."
                );
              }
            }
          }
          activity_errors_holder[index] = business_activity_errors;
          index = index + 1;
        }
      }

      if (Object.entries(business_details_errors.value).length > 0) {
        this.$store.commit("setStepTwoErrors", business_details_errors);
        isBusinessDetailsClean = false;
      } else if (!this.detailsHasError) {
        this.$store.commit("setStepTwoErrors", {
          key: "business_details",
          value: {},
        });
      }

      if (Object.entries(activity_errors_holder).length > 0) {
        Object.keys(activity_errors_holder).forEach((item) => {
          if (Object.entries(activity_errors_holder[item].value).length > 0) {
            isBusinessActivitiesClean = false;
          }
        });
        if (!isBusinessActivitiesClean) {
          this.$store.commit("setActivityErrors", activity_errors_holder);
        }
        {
          this.$store.commit("setActivityErrors", {});
        }
      }

      if (
        isBusinessDetailsClean &&
        isBusinessActivitiesClean &&
        !this.detailsHasError &&
        !this.lessorDetailsHasError
      ) {
        await this.sendBusinessLineToLGU();
        this.$store.commit("setCurrentApplicationStep", "3");
      } else {
        this.$swal({
          title: "Failed!",
          text:
            "Please fix the validation errors before proceeding to the next step.",
          icon: "error",
        });
      }
    },
    async sendBusinessLineToLGU() {
      const config = {
        headers: {
          "OneDoc-Token": oneDocToken,
          "Content-Type": "application/json",
        },
      };

      const businessLineObj = {};
      if (this.businessActivities && this.businessActivities.length > 0) {
        this.businessActivities.forEach((item, index) => {
          businessLineObj[index + 1] = {
            name: item.line_of_business,
            unitcount: parseInt(item.units),
            grossamount: parseFloat(item.capitalization),
            capital: parseFloat(item.capitalization),
          };
        });

        const data = {
          name: "POSTBusinessLines",
          param: {
            onlinerefno: this.businessBasicInformation.reference_number || "",
            businesslines: businessLineObj,
          },
        };

        // to update
        try {
          const response = await axios.post(
            `${lguLocalEndpoint}`,
            data,
            config
          );

          if (response.data.Result) {
            return true;
          } else {
            return false;
          }
        } catch (error) {
          console.log(error);
        }
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.meta-error-text {
  margin-bottom: 10px;
  font-size: 12px;
  color: #940000;
  font-weight: bold;
}
.add-icon {
  text-align: right;
  font-size: 25px;
  padding: 10px 0px 10px 10px;
  cursor: pointer;
  color: #2699fb;
  position: absolute;
  right: 0;
  top: -10px;
}
div.meta-container {
  width: 100%;
  padding: 50px;
  background-color: #e8726f;
  box-shadow: 2px 8px 12px 0px gray;
  color: whitesmoke;
  h1.meta-form-title {
    margin-bottom: 40px;
  }
  div.meta-form-group {
    width: 100%;
    div.meta-group-title {
      color: whitesmoke;
      font-size: 16px;
      line-height: 19px;
      width: 100%;
      margin-bottom: 20px;
      margin-top: 30px;
    }
    div.meta-input-label {
      color: whitesmoke;
    }
    div.input-wrapper {
      margin-bottom: 15px;
    }
    div.meta-input-group {
      width: 100%;
      .input-w2 {
        width: 50%;
        float: left;
        margin-right: 10px;
      }
      .input-w3 {
        width: 33%;
        float: left;
        margin-right: 10px;
      }
      .input-w4 {
        width: 25%;
        float: left;
        margin-right: 10px;
      }
      .input-w3:last-child,
      .input-w4:last-child,
      .input-w2:last-child {
        margin-right: 0;
      }

      .input-phone {
        width: 60%;
      }
    }

    div.meta-multi-group {
      padding: 30px;
      background-color: whitesmoke;
      border-radius: 15px;
      margin-bottom: 20px;
      box-sizing: border-box;
      div.meta-group-title {
        font-size: 15px;
      }
      div.meta-input-label {
        color: #2b2b2b !important;
      }
      .mb30 {
        margin-bottom: 35px;
      }
    }
  }
  div.button-left-right {
    .back-button {
      float: left;
      background-color: #73befc;
      border-color: #73befc;
    }
    .next-button {
      float: right;
    }
  }
}

.back-button:hover {
  background-color: #2699fb !important;
  color: #fff !important;
  border-color: #2699fb !important;
}

.p-relative {
  position: relative;
}

.no-mt {
  margin-top: 0 !important;
}

.gross-monthly-rental-input {
  box-sizing: border-box;
}

.capitalization-input {
  box-sizing: border-box;
}

/*
MOBILE RESPONSIVENESS 
--------------------------------------------------------------*/

@media only screen and (max-width: 1380px) {
  div.meta-container h1.meta-form-title {
    font-size: 22px;
  }
}

@media only screen and (max-width: 768px) {
  div.meta-container h1.meta-form-title {
    font-size: 20px;
  }

  .input-phone {
    margin-bottom: 8px;
  }

  div.meta-container div.meta-form-group div.meta-group-title {
    font-size: 15px;
    margin-bottom: 10px;
  }

  div.meta-container div.meta-form-group div.meta-input-group .input-w3 {
    width: 100%;
    float: left;
    margin-right: 0;
    flex-direction: unset;
  }

  div.meta-container div.meta-form-group div.meta-input-group.flex-row.w2,
  div.meta-container div.meta-form-group div.meta-input-group.flex-row.w3,
  div.meta-container div.meta-form-group div.meta-input-group.flex-row.w4 {
    width: 100%;
    flex-direction: unset;
    flex-wrap: wrap;
    margin-right: 0;
  }

  div.meta-container div.meta-form-group div.meta-input-group .input-w4,
  div.meta-container div.meta-form-group div.meta-input-group .input-w2 {
    width: 100%;
    margin-right: 0;
  }

  div.meta-container
    div.meta-form-group
    div.meta-input-group
    .input-w4:nth-child(even) {
    margin-right: 0;
  }
}

@media only screen and (max-width: 650px) {
  div.meta-container {
    padding: 40px 30px;
  }

  div.meta-container h1.meta-form-title {
    font-size: 18px;
    margin-bottom: 30px;
  }
}

@media only screen and (max-width: 480px) {
  div.meta-container {
    padding: 30px 15px;
  }

  div.meta-container div.meta-form-group.mb60 {
    margin-bottom: 20px;
  }

  div.meta-container h1.meta-form-title {
    font-size: 16px;
  }

  div.meta-container div.meta-form-group div.meta-group-title {
    font-size: 14px;
    margin-bottom: 15px;
  }

  div.meta-container div.button-left-right .back-button {
    background-color: #048cff;
    border-color: #73befc;
    width: auto;
    background: transparent;
    border: none;
    box-shadow: none;
    color: #2699fb;
    min-width: unset;
  }

  div.meta-container div.button-left-right .next-button {
    width: auto;
    background: transparent;
    border: none;
    box-shadow: none;
    min-width: unset;
    color: #2699fb;
  }

  div.meta-container div.meta-form-group div.meta-multi-group {
    padding: 15px;
  }
}
</style>
